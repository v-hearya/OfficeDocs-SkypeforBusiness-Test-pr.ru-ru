﻿---
title: Использование командлетов Lync Online в сочетании с другими командлетами Windows PowerShell
TOCTitle: Использование командлетов Lync Online в сочетании с другими командлетами Windows PowerShell
ms:assetid: 8bb8800a-f966-4570-8c8b-db87a91ad783
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn362816(v=OCS.15)
ms:contentKeyID: 56270587
ms.date: 06/01/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Использование командлетов Lync Online в сочетании с другими командлетами Windows PowerShell

 

_**Дата изменения раздела:** 2015-06-22_

При подключении к Skype для бизнеса Online с помощью Windows PowerShell доступны для использования примерно 40 командлетов Skype для бизнеса Online. Однако при управлении Skype для бизнеса Online вы не ограничены только этими 40 командлетами. Помимо командлетов Skype для бизнеса Online, вы также можете использовать любые другие командлеты Windows PowerShell, установленные на вашем компьютере. (При установке Windows PowerShell 3.0 устанавливаются сотни базовых командлетов Windows PowerShell.) В своих командах вы можете использовать командлеты Skype для бизнеса Online в сочетании с любыми другими командлетами, доступными на компьютере.

Хотя полное рассмотрение оболочки Windows PowerShell 3.0 выходит за рамки этой статьи, ниже приведено несколько примеров того, как можно использовать командлеты в сочетании друг с другом. Во-первых, ни в одном из командлетов Skype для бизнеса Online нет команды "Печать". Вы также не найдете ее в консоли Windows PowerShell. Так как же напечатать информацию, возвращенную командлетом? Одним из способов является передача этой информации в командлет **Out-Printer**.

    Get-CsTenant | Out-Printer

Так как дополнительные параметры не используются, вся информация, возвращенная командлетом **the Out-Printer**, будет напечатана с помощью принтера по умолчанию.

Аналогичным образом, ни у одного из командлетов Skype для бизнеса Online нет параметра, позволяющего сохранять данные в файл. Но это не проблема: в приведенной ниже команде возвращенные сведения сохраняются в текстовом файле C:\\Logs\\Tenants.txt с помощью командлета **Out-File**.

    Get-Tenant | Out-File -FilePath "C:\Logs\Tenants.txt"

А в этой команде возвращаемые и выводимые на экран данные ограничиваются с помощью командлета **Select-Object**. В данном примере командлет [Get-CsOnlineUser](get-csonlineuser.md) возвращает сведения для всех пользователей Skype для бизнеса Online, а затем с помощью командлета **Select-Object** выводимые данные ограничиваются значением параметра Identity пользователя и его политикой архивации.

    Get-CsOnlineUser | Select-Object Identity, ArchivingPolicy

Так как на вашем компьютере будут доступны для использования сотни командлетов, может быть непросто определить, какие из них являются командлетами Skype для бизнеса Online, а какие нет. Чтобы получить список командлетов Skype для бизнеса Online (и только командлетов Skype для бизнеса Online), сначала нужно определить имя временного модуля Windows PowerShell, который содержит все командлеты Skype для бизнеса Online. Для этого в командной строке Windows PowerShell выполните следующую команду:

    Get-Module

На экране появятся примерно следующие данные:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

Командлеты Skype для бизнеса Online содержатся в модуле, свойство ModuleType которого имеет значение Script. Чтобы получить список этих командлетов, выполните командлет **Get-Command**, используя в качестве имени модуля имя модуля сценария.

    Get-Command -Module tmp_5astd3uh.m5v

Не исключено, что свойство ModuleType сразу нескольких модулей будет иметь значение Script. В этом случае можно выполнить следующую команду, чтобы узнать, какой модуль содержит командлеты **Get-CsTenant**.

    Get-Command Get-CsTenant

Модуль, возвращенный командлетом **Get-CsTenant**, и будет модулем, содержащим все командлеты Skype для бизнеса Online.

    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Function        Get-CsTenant                                       tmp_5astd3uh.m5v

## См. также

#### Концепции

[Введение в Windows PowerShell и Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)


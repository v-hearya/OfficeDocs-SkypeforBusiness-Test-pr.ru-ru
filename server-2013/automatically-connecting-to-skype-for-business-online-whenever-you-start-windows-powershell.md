﻿---
title: Автоматическое подключение к Lync Online при каждом запуске Windows PowerShell
TOCTitle: Автоматическое подключение к Lync Online при каждом запуске Windows PowerShell
ms:assetid: 68f76c36-5dd6-48ea-b19a-d65593199e4c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn362799(v=OCS.15)
ms:contentKeyID: 56270571
ms.date: 06/01/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Автоматическое подключение к Lync Online при каждом запуске Windows PowerShell

 

_**Дата изменения раздела:** 2015-06-22_

Если вы не помните все командлеты, необходимые для подключения к системе Skype для бизнеса Online, среду можно настроить таким образом, чтобы для подключения к Skype для бизнеса Online было достаточно щелкнуть ярлык и ввести пароль Skype для бизнеса Online.

Для этого сначала откройте блокнот (или любой другой текстовый редактор) и вставьте следующие команды, заменяя kenmyer@litwareinc.com именем своей учетной записи Skype для бизнеса Online:

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $session = New-CsOnlineSession -Credential $credential 
    Import-PSSession $session

Сохраните файл с расширением PS1 (например, C:\\Scripts\\LyncOnline.ps1).

После сохранения файла выполните указанные ниже действия, чтобы создать на рабочем столе ярлык, который запускает Windows PowerShell и выполняет при запуске созданный сценарий.

1.  Щелкните рабочий стол правой кнопкой мыши, выберите команды **Создать** и **Ярлык**.

2.  В мастере **Создание ярлыка** введите следующие данные в поле **Укажите размещение объекта** и нажмите кнопку **Далее** (при этом укажите путь к созданному файлу сценария):
    
        powershell.exe -noexit C:\Scripts\LyncOnline.ps1

3.  В поле **Введите имя ярлыка** введите название своего ярлыка (например, **Skype для бизнеса Online**) и нажмите кнопку **Готово**.

4.  В следующий раз, когда вам потребуется запустить Windows PowerShell для управления средой Skype для бизнеса Online, просто дважды щелкните новый ярлык и введите пароль. Сценарий автоматически создаст подключение и настроит новый удаленный сеанс.

Этот новый сеанс скорее всего не будет сохранен в переменной $session. Вместо этого ему будет присвоен идентификатор 1. Это не повлияет на работоспособность сеанса до момента его завершения. Для этого при вызове командлета **Remove-PSSession** потребуется указать идентификатор данного сеанса:

    Remove-PSSession 1

Чтобы уточнить идентификатор сеанса Skype для бизнеса Online, выполните в командной строке Windows PowerShell следующую команду:

    Get-PSSession

## См. также

#### Концепции

[Настройка компьютера для управления Lync Online](configuring-your-computer-for-skype-for-business-online-management.md)


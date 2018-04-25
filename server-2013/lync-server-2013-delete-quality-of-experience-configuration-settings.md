﻿---
title: Удаление параметров настройки для качества взаимодействия
TOCTitle: Удаление параметров настройки для качества взаимодействия
ms:assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182613(v=OCS.15)
ms:contentKeyID: 49311770
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Удаление параметров настройки для качества взаимодействия

 

_**Дата изменения раздела:** 2013-02-23_

Показатели качества взаимодействия (QoE) отслеживают качество звуковых и голосовых вызовов в вашей организации, в том числе количество потерянных пакетов, фоновый шум и объем "помех" (отличий в задержке пакетов). Эти показатели хранятся в базе данных отдельно от других данных (таких как записи сведений о вызовах), что позволяет включать и отключать QoE независимо от записи других данных.

При установке Microsoft Lync Server 2013 создается отдельная глобальная коллекция параметров конфигурации качества взаимодействия. Администраторы также могут создавать настраиваемые коллекции параметров, которые можно применять к отдельным сайтам. Параметры, настроенные на уровне сайта имеют более высокий приоритет, чем параметры, настроенные в глобальной области. В случае удаления параметров уровня сайта качество взаимодействия на этом сайте будет управляться с использованием глобальных параметров.

Помните, что вы также можете "удалить" глобальные параметры. Однако фактическое удаление глобальных параметров при этом не выполняется. Вместо этого все свойства в этой коллекции сбрасываются на значения по умолчанию. Например, по умолчанию в коллекции параметров конфигурации качества взаимодействия включена очистка. Предположим, что вы изменяете глобальную коллекцию, чтобы отключить очистку. Если вы позднее удаляете глобальные параметры, все свойства будут сброшены в значения по умолчанию. В данном случае это означает, что очистка будет снова включена.

Вы можете удалить параметры конфигурации качества взаимодействия с помощью панели управления Lync Server или командлета [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md).

## Удаление параметров конфигурации качества взаимодействия с помощью панели управления Lync Server

1.  Войдите на компьютер как член группы RTCUniversalServerAdmins или роли CsVoiceAdministrator, CsServerAdministrator или CsAdministrator. Дополнительные сведения см. в разделе [Делегирование разрешений на установку в Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните **Мониторинг и архивация** и затем выберите **Данные о качестве взаимодействия**.

4.  На странице **Данные о качестве взаимодействия** щелкните требуемую политику, щелкните элементы **Изменить** и **Удалить**.

5.  Нажмите кнопку **ОК**.

## Удаление параметров конфигурации качества взаимодействия с помощью командлетов командной консоли Командная консоль Lync Server

Вы также можете удалить параметры конфигурации качества взаимодействия с помощью командной консоли Командная консоль Lync Server и командлета **Remove-CsQoEConfiguration**. Этот командлет можно выполнить из командная консоль Lync Server 2013 или из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Удаление указанной коллекции параметров конфигурации качества взаимодействия

  - Эта команда удаляет параметры конфигурации качества взаимодействия, примененные к сайту Redmond:
    
        Remove-CsQoEConfiguration -Identity "site:Redmond"

## Удаление всех параметров конфигурации качества взаимодействия, примененных на уровне сайта

  - Эта команда удаляет все параметры конфигурации качества взаимодействия, примененные на уровне сайта:
    
        Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration

## Удаление всех параметров конфигурации качества взаимодействия с отключенным наблюдением за качеством взаимодействия

  - Эта команда удаляет все параметры конфигурации качества взаимодействия с отключенным наблюдением за качеством взаимодействия:
    
        Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration

Дополнительные сведения см. в разделе [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md).

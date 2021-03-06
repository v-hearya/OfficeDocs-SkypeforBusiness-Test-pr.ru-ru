﻿---
title: Disable-CsPublicProvider
TOCTitle: Disable-CsPublicProvider
ms:assetid: df1338ea-fe6d-45da-a39c-86108bb54ef5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398984(v=OCS.15)
ms:contentKeyID: 49311397
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsPublicProvider

 

_**Дата изменения раздела:** 2015-03-09_

Отключает общедоступного поставщика, настроенного для использования в организации. Общедоступный поставщик — это организация, которая обеспечивает обмен мгновенными сообщениями, сведения о присутствии и другие схожие услуги для неограниченного круга лиц. Lync Server поставляется с тремя настроенными, но не включенными поставщиками: Yahoo, AIM (AOL) и Messenger (MSN). Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    Disable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Disable-CsPublicProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Примеры

## ПРИМЕР 1

В примере 1 отключается общедоступный поставщик с удостоверением Messenger. Если поставщик MSN уже отключен, то команда будет возвращать ошибку.

    Disable-CsPublicProvider -Identity "Messenger"

## ПРИМЕР 2

В примере 2 отключаются все включенные в текущий момент общедоступные поставщики. Для этого сначала с помощью командлета **Get-CsPublicProvider** извлекается коллекция всех общедоступных поставщиков, используемых в текущий момент в организации. Затем эта коллекция передается в командлет **Where-Object**, который отбирает только тех поставщиков, свойство Enabled которых имеет значение True. Затем эта отфильтрованная коллекция передается в командлет **Disable-CsPublicProvider**, который отключает всех поставщиков в коллекции.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $True} | Disable-CsPublicProvider

## ПРИМЕР 3

Команда, показанная в примере 3, отключает всех общедоступных поставщиков, которые в текущий момент включены и имеют уровень проверки AlwaysVerifiable. Для выполнения этой задачи сначала вызывается командлет **Get-CsPublicProvider**, который возвращает коллекцию всех общедоступных поставщиков, в текущий момент использующихся в организации. Затем эта коллекция передается в командлет **Where-Object**, который выбирает поставщиков, удовлетворяющих двум условиям: 1) свойство VerificationLevel имеет значение AlwaysVerifiable; 2) свойство Enabled имеет значение True. (Оператор -and говорит командлету **Where-Object**, что выбираемые объекты должны соответствовать всем указанным критериям.) Затем отфильтрованная коллекция передается в командлет **Disable-CsPublicProvider**, который отключает каждого поставщика в коллекции.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable" -and $_.Enabled -eq $True} | Disable-CsPublicProvider

## Подробное описание

Федерация позволяет двум организациям установить отношение доверия, которое облегчает взаимодействие между двумя группами. Если федерация установлена, пользователи в этих двух организациях могут обмениваться мгновенными сообщениями, подписываться на уведомления о присутствии, а также взаимодействовать другими способами с помощью приложений SIP, таких как Lync 2013. Lync Server поддерживает три типа федерации: 1) прямую федерацию между двумя организациями; 2) федерацию между организацией и общедоступным поставщиком; 3) федерацию между организацией и сторонним поставщиком услуг размещения.

Общедоступный поставщик — это организация, которая предоставляет услуги связи SIP (Session Initiation Protocol) неограниченному кругу лиц. При установке федеративных отношений с общедоступным поставщиком фактически устанавливаются отношения со всеми пользователями, учетные записи которых размещаются этим поставщиком. Например, если вы установите федеративные отношения с Messenger (MSN), ваши пользователи смогут обмениваться мгновенными сообщениями и сведениями о присутствии со всеми, у кого есть учетная запись службы мгновенных сообщений Messenger.

Для установки федеративных отношений с общедоступным поставщиком необходимо создать и включить нового общедоступного поставщика. (Кроме того, общедоступному поставщику придется создать с вами федеративные отношения.) При создании общедоступного поставщика имеется возможность либо включить, либо отключить эти федеративные отношения. Если общедоступный поставщик включен, то пользователи в вашей организации будут иметь возможность обмениваться мгновенными сообщениями и сведениями о присутствии с пользователями, которые имеют учетные записи у этого общедоступного поставщика. Если общедоступный поставщик отключен, то возможность установки связи с пользователями, которые имеют учетные записи у этого общедоступного поставщика, будет приостановлена, и останется приостановленной до тех пор, пока этот поставщик не будет включен. Если нужно временно приостановить федеративные отношения, это можно сделать с помощью командлета **Disable-CsPublicProvider**. Если вы предпочитаете полностью удалить поставщика, используйте командлет **Remove-CsPublicProvider**.

По умолчанию право на локальный запуск командлета **Disable-CsPublicProvider** имеют члены группы RTCUniversalServerAdmins. Чтобы получить список всех ролей управления доступом на основе ролей (RBAC), которым назначен этот командлет (включая все самостоятельно созданные роли RBAC), выполните в командной строке Windows PowerShell следующую команду:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Disable-CsPublicProvider"}

## Параметры


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Обязательный?</th>
<th>Тип</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Запрашивает подтверждение перед выполнением команды.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Подавляет отображение любых сообщений о некритических ошибках, которые могут возникать при выполнении этой команды.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Уникальный идентификатор отключаемого общедоступного поставщика. Обычно это имя веб-сайта, предоставляющего услуги (например, Yahoo!; AOL; MSN и др.).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Объект DisplayPublicProvider</p></td>
<td><p>Позволяет передать в командлет ссылку на объект вместо задания значений отдельных параметров.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Описывает, что произойдет при выполнении команды без реального выполнения команды.</p></td>
</tr>
</tbody>
</table>


## Типы входных данных

Объект Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider. Командлет **Disable-CsPublicProvider** принимает в качестве входных данных экземпляры объекта общедоступного поставщика, переданные по конвейеру.

## Типы возвращаемых данных

Нет. Этот командлет отключает экземпляры объекта Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## См. также

#### Другие ресурсы

[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)


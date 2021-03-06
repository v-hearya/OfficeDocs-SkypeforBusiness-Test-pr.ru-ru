﻿---
title: New-CsClientPolicyEntry
TOCTitle: New-CsClientPolicyEntry
ms:assetid: e975d048-4911-4ae6-9446-2a6363726a4a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg399046(v=OCS.15)
ms:contentKeyID: 49311538
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientPolicyEntry

 

_**Дата изменения раздела:** 2015-03-09_

Добавляет новые функции к политикам клиента Lync Server. Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    New-CsClientPolicyEntry -Name <String> -Value <String>

## Примеры

## ПРИМЕР 1

Команды, представленные в примере 1, показывают, каким образом можно добавить новый элемент политики к глобальной политике клиента. В этом примере добавляется новая функция обратной связи для Lync. Обратите внимание, что данный пример приведен только в демонстрационных целях. Не следует предполагать, что вы сможете выполнить эти команды и добавить аналогичную функцию обратной связи к вашей копии Lync.

Чтобы добавить новый элемент политики, первая команда в этом примере использует командлет **New-CsClientPolicyEntry** для создания записи с именем OnlineFeedbackURL и значения http://www.litwareinc.com/feedback. Итоговый объект элемента политики сохраняется в переменной с именем $x.

Во второй команде командлет **Get-CsClientPolicy** используется для создания ссылки на объект ($y) для глобальной политики клиента. После создания ссылки на объект используется метод Add для добавления нового элемента политики к свойству PolicyEntry. Если свойство PolicyEntry уже обладает одним или несколькими элементами, новое значение просто добавляется в конец этой коллекции.

И, наконец, последняя команда в этом примере использует командлет **Set-CsClientPolicy** для записи изменений в действительную глобальную политику. Если вызов командлета **Set-CsClientPolicy** не осуществляется, изменения сохраняются только в памяти и удаляются после завершения сеанса Windows PowerShell или удаления переменной $x.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    
    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.Add($x)
    
    Set-CsClientPolicy -Instance $y

## ПРИМЕР 2

Пример 2 представляет собой вариант команды, представленной в примере 1. Однако в данном случае новый элемент политики заменяет все элементы, существующие в данный момент в свойстве PolicyEntry глобальной политики. Для этого первая команда в данном примере создает новый объект политики, который сохраняется в переменной с именем $x. Затем вторая команда использует командлет **Set-CsClientPolicy**, чтобы задать $x в качестве значения свойства PolicyEntry. После завершения выполнения этой команды единственным элементом в свойстве PolicyEntry будет новый элемент. Все элементы, содержащиеся в данном свойстве до вызова командлета **Set-CsClientPolicy**, заменяются новым элементом.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    Set-CsClientPolicy -Identity global -PolicyEntry $x

## ПРИМЕР 3

Пример 3 показывает, как удалить элемент политики клиента из глобальной политики. Для этого первая команда в примере загружает политику глобального клиента и сохраняет эту информацию в переменной с именем $y.

После загрузки глобальной политики вторая команда в этом примере использует метод RemoveAt() для удаления первого элемента политики в данной политике. Удаляемый элемент политики обозначается порядковым номером: первому элементу политики присваивается порядковый номер 0, второму элементу политики — порядковый номер 1, и так далее. Синтаксис RemoveAt (0) означает, что первый элемент политики будет удален.

При удалении этого элемента политики из экземпляра глобальной политики во внутренней памяти вызывается командлет **Set-CsClientPolicy** для записи этих изменений в действительный экземпляр глобальной политики клиента.

    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.RemoveAt(0)
    
    Set-CsClientPolicy -Instance $y 

## ПРИМЕР 4

Команда, представленная в примере 4, удаляет все элементы клиентской политики, настроенные для глобальной политики. Это осуществляется путем использования параметра PolicyEntry и установки нулевого ($Null) значения параметра.

    Set-CsClientPolicy -Identity global -PolicyEntry $Null

## Подробное описание

Клиентские политики являются основным механизмом, используемым Lync Server для управления клиентским программным обеспечением, таким как Lync. При создании или настройке клиентской политики предоставляются различные варианты для выбора; например, можно указать, используются ли фотографии в Lync, разрешены ли значки настроения в мгновенных сообщениях и будет ли Lync автоматически сохранять протоколы сеансов мгновенного обмена сообщениями. Эти варианты позволяют задавать различные параметры, имеющие отношение к клиенту, которыми должен управлять оператор.

Однако они не могут включать все параметры клиентов, управление которыми осуществляется клиентом. Чтобы повысить гибкость управления и возможности расширения, политики клиента включают свойство PolicyEntry. Это многозначное свойство позволяет администраторам добавлять новые возможности управления, которые не вызываются явным образом в клиентской политике. Например, перед выпуском Lync Server бета-тестировщикам предоставляется возможность добавления функции обратной связи к Lync. Эта функция была добавлена как новый элемент политики и создана с помощью командлета **New-CsClientPolicyEntry**.

Обратите внимание, что нельзя произвольно создавать новые элементы политики, предполагая, что эти элементы будут управлять Lync или некоторыми другими клиентскими приложениями. Вместо этого необходимо дождаться получения уведомление от корпорации Майкрософт относительно названий и значений, которые можно использовать для создания новых элементов политики клиента.

По умолчанию право на локальный запуск командлета **New-CsClientPolicyEntry** имеют члены группы RTCUniversalServerAdmins. Чтобы получить список всех ролей управления доступом на основе ролей (RBAC), которым назначен этот командлет (включая все самостоятельно созданные роли RBAC), выполните в командной строке Windows PowerShell следующую команду:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientPolicyEntry"}

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
<td><p><em>Name</em></p></td>
<td><p>Обязательный</p></td>
<td><p>System.String</p></td>
<td><p>Имя нового элемента политики. Например: -Name &quot;OnlineFeedbackURL&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Value</em></p></td>
<td><p>Обязательный</p></td>
<td><p>System.String</p></td>
<td><p>Значение, которое необходимо назначить новому элементу политики. Например: -Value http://www.litwareinc.com/feedback.</p></td>
</tr>
</tbody>
</table>


## Типы входных данных

Нет. Командлет New-CsClientPolicyEntry не принимает входные данные из конвейера.

## Типы возвращаемых данных

Командлет **New-CsClientPolicyEntry** создает новые экземпляры объекта Microsoft.Rtc.Management.WritableConfig.Policy.Client.PolicyEntryType.

## См. также

#### Другие ресурсы

[New-CsClientPolicy](new-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)


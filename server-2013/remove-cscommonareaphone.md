﻿---
title: Remove-CsCommonAreaPhone
TOCTitle: Remove-CsCommonAreaPhone
ms:assetid: f2c93bec-4b99-4b69-abe0-d2d9e33dcadd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg413016(v=OCS.15)
ms:contentKeyID: 49311644
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCommonAreaPhone

 

_**Дата изменения раздела:** 2015-03-09_

Removes an existing common area phone from the collection of phones managed by using Lync Server. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    Remove-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## Examples

## EXAMPLE 1

The command shown in Example 1 deletes the common area phone that has the display name "Building 14 Lobby". To do this, the command first calls the **Get-CsCommonAreaPhone** cmdlet along with the Filter parameter and the filter value "{DisplayName -eq "Building 14 Lobby"}". The returned object is then piped to, and deleted by, the **Remove-CsCommonAreaPhone** cmdlet.

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"} | Remove-CsCommonAreaPhone

## EXAMPLE 2

In Example 2, the command deletes all the common area phones that have not been assigned a dial plan. This task is carried out by first using the **Get-CsCommonAreaPhone** cmdlet and the Filter parameter to return the specified items; the filter value {DialPlan -eq $Null} limits the returned data to common area phones that have not been assigned a dial plan. This filtered collection is then piped to the **Remove-CsCommonAreaPhone** cmdlet, which deletes each phone in the collection.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null} | Remove-CsCommonAreaPhone

## EXAMPLE 3

Example 3 deletes all the common area phones that have contact objects located in the Redmond OU in Active Directory. To carry out this task, the **Get-CsCommonAreaPhone** cmdlet is first called in order to return all the common area phones with contact objects in the Redmond OU; the OU parameter and the parameter value "ou=Redmond,dc=litwareinc,dc=com” is used to limit the returned data to the specified organizational unit. The returned collection is then piped to the **Remove-CsCommonAreaPhone** cmdlet, which deletes each phone in that collection.

    Get-CsCommonAreaPhone -OU "ou=Redmond,dc=litwareinc,dc=com" | Remove-CsCommonAreaPhone

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone’s office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that’s because phone use in Lync Server is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.

One solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) For example, this command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

From time-to-time you might need to delete the contact object associated with a common area phone. For example, if you remove the phone from an employee lounge then there is no need to have a contact object associated with that phone. The **Remove-CsCommonAreaPhone** cmdlet provides a way for you to delete common area phones. When you run this cmdlet, the phone will be deleted from the list of common area phones returned by the **Get-CsCommonAreaPhone** cmdlet. In addition, the contact object associated with that phone will be deleted from Доменные службы Active Directory.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsCommonAreaPhone** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational units (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCommonAreaPhone"}

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
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Unique identifier for the common area phone. Common area phones are identified using the Active Directory distinguished name of the associated contact object. By default, common area phones use a globally unique identifier (GUID) as their common name, which means phones will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Because of that, you might find it easier to retrieve common area phones by using the <strong>Get-CsCommonAreaPhone</strong> cmdlet, and then piping the returned objects to the <strong>Remove-CsCommonAreaPhone</strong> cmdlet.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Запрашивает подтверждение перед выполнением команды.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Описывает, что произойдет при выполнении команды без реального выполнения команды.</p></td>
</tr>
</tbody>
</table>


## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object. The **Remove-CsCommonAreaPhone** cmdlet accepts pipelined instances of the common area phone object.

## Return Types

The **Remove-CsCommonAreaPhone** cmdlet deletes existing instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

## См. также

#### Другие ресурсы

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)


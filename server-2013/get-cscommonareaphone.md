﻿---
title: Get-CsCommonAreaPhone
TOCTitle: Get-CsCommonAreaPhone
ms:assetid: bfb7927b-49a7-4637-a9ff-fd68897efb45
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412934(v=OCS.15)
ms:contentKeyID: 49311049
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCommonAreaPhone

 

_**Дата изменения раздела:** 2015-03-09_

Возвращает сведения о телефонах общего пользования, управление которыми осуществляется с помощью Lync Server. Телефоны общего пользования — это телефоны, установленные в вестибюлях зданий, комнатах отдыха или других местах, где они используются широким кругом людей для разных целей. Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    Get-CsCommonAreaPhone [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## Примеры

## ПРИМЕР 1

Команда, показанная в примере 1, возвращает сведения о всех телефонах общего пользования, настроенных для использования в организации. Для этого вызывается командлет **Get-CsCommonAreaPhone** без параметров.

    Get-CsCommonAreaPhone

## ПРИМЕР 2

В примере 2 возвращаются сведения о телефоне общего пользования с отображаемым именем Active Directory "Building 14 Lobby". Для этого используется параметр Filter со значением фильтра {DisplayName -eq "Building 14 Lobby"}. Это значение ограничивает возвращаемые объекты только теми телефонами общего пользования, свойство DisplayName которых равно "Building 14 Lobby".

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"}

## ПРИМЕР 3

В примере 3 возвращаются все телефоны общего пользования, отображаемые имена Active Directory которых начинаются со строки "Building 14". Для этого вызывается командлет **Get-CsCommonAreaPhone** с параметром Filter, для которого задано значение {DisplayName -like "Building 14\*"}. В значении фильтра используется оператор -like и строка шаблона "Building 14\*" для ограничения возвращаемых данных только теми телефонами, значения свойства DisplayName которых начинаются со строки "Building 14" (например, "Building 14 Lobby", "Building 14 Cafeteria" и т. д.).

    Get-CsCommonAreaPhone  -Filter {DisplayName -like "Building 14*"}

## ПРИМЕР 4

В примере 4 возвращается отдельный телефон общего пользования, свойство LineUri которого имеет значение "tel:+14255551234". Поскольку значение свойства LineUris должно быть уникальным, эта команда всегда возвращает только один объект.

    Get-CsCommonAreaPhone  -Filter {LineUri -eq "tel:+14255551234"}

## ПРИМЕР 5

Команда, показанная в примере 5, возвращает сведения о всех телефонах общего пользования, которым не была назначена абонентская группа. Для этого используется параметр Filter со значением {DialPlan -eq $Null}. Он ограничивает возвращаемые данные только теми телефонами, свойство DialPlan которых имеет значение null. Если телефону общего пользования явным образом не назначена абонентская группа, для него автоматически используется глобальная абонентская группа или, если таковой не существует, абонентская группа, назначенная сайту.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null}

## ПРИМЕР 6

В примере 6 возвращается коллекция, включающая все телефоны общего пользования, которые имеют контактный объект в подразделении Telecommunications в доменных службах Доменные службы Active Directory. Для этого вызывается командлет **Get-CsCommonAreaPhone** с параметром OU. Значение параметра ограничивает возвращаемые данные только теми телефонами, которые имеют контактные объекты в подразделении с различающимся именем ou=Telecommunications,dc=litwareinc,dc=com.

    Get-CsCommonAreaPhone -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## Подробное описание

Телефоны общего пользования — это IP-телефоны, не предназначенные для применения отдельным пользователем. Телефоны общего пользования обычно располагаются не в чьем-то кабинете, а в приемных, кафетериях, комнатах отдыха, переговорных и других местах, где обычно собирается большое количество людей. Так как в Lync Server управление телефонами обычно осуществляется на основе политик голосовых вызовов и абонентских групп, назначаемых отдельным пользователям, то управление подобными телефонами будет представлять для администраторов непростую задачу.

Решением этой задачи является создание контактных объектов Active Directory для всех телефонов общего пользования. (Эти контактные объекты можно создать с помощью командлета **New-CsCommonAreaPhone**.) Так же как и учетным записям пользователей, этим контактным объектам можно назначать политики и планы голосовой связи. Это позволяет обеспечить контроль над телефонами общего пользования несмотря на то, что они не связаны с отдельным пользователем. Например, чтобы запретить переключение или парковку вызовов, выполняемых с телефона общего пользования, можно создать соответствующую политику голосовой связи и затем назначить ее телефону общего пользования (или, если точнее, представляющему его контактному объекту). Например, следующая команда назначает политику голосовой связи CommonAreaPhoneVoicePolicy всем телефонам общего пользования.

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

Командлет **Get-CsCommonAreaPhone** позволяет извлекать сведения о телефонах общего пользования, настроенных для использования в организации. Если вызвать командлет **Get-CsCommonAreaPhone** без параметров, он вернет сведения о всех телефонах общего пользования. Дополнительные параметры обеспечивают различные способы фильтрации данных. Например, можно получить сведения о всех телефонах общего пользования, которые имеют контактные объекты в указанном подразделении, или о всех контактных объектах в указанном здании.

По умолчанию право на локальный запуск командлета **Get-CsCommonAreaPhone** имеют члены следующих групп: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. Разрешения на запуск этого командлета для конкретных сайтов или подразделений Active Directory можно назначать с помощью командлета **Grant-CsOUPermission**. Чтобы получить список всех ролей управления доступом на основе ролей (RBAC), которым назначен этот командлет (включая все самостоятельно созданные роли RBAC), выполните в командной строке Windows PowerShell следующую команду:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCommonAreaPhone"}

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
<th>Обязательный</th>
<th>Тип</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Credential</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Позволяет запускать командлет <strong>Get-CsCommonAreaPhone</strong> с другими учетными данными. Используется, когда у учетной записи, с использованием которой был выполнен вход в Windows, нет необходимых прав для работы с объектами контактов.</p>
<p>Для использования параметра Credential сначала требуется создать объект PSCredential с помощью командлета <strong>Get-Credential</strong>. Дополнительные сведения см. в разделе справки, посвященном командлету <strong>Get-Credential</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Позволяет подключиться к определенному контроллеру домена для получения контактных данных. Для подключения к определенному контроллеру используйте параметр DomainController, указав после него полное доменное имя соответствующего компьютера (например, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.String</p></td>
<td><p>Позволяет ограничить возвращаемые данные, фильтруя их по атрибутам, связанным с Lync Server. Например, можно ограничить возвращаемые данные контактными объектами телефонов общего пользования, которым назначена определенная политика голосовой связи, или контактами, которым не назначена определенная политика голосовой связи.</p>
<p>Параметр Filter использует тот же синтаксис фильтрации Windows PowerShell, что и командлет <strong>Where-Object</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Уникальный идентификатор телефона общего пользования. Телефоны общего пользования идентифицируются по различающемуся имени Active Directory соответствующего контактного объекта. По умолчанию в качестве общего имени телефона общего пользования используется глобальный уникальный идентификатор (GUID). Это означает, что идентификатор телефона, как правило, выглядит следующим образом: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.String</p></td>
<td><p>Позволяет ограничить возвращаемые данные путем фильтрации по универсальным атрибутам Active Directory (т. е. атрибутам, которые не связаны именно с Lync Server). Например, можно ограничить возвращаемые данные объектами контактов, которые назначены конкретному отделу или расположены в конкретном здании.</p>
<p>В параметре LdapFilter для создания фильтров используется язык запросов LDAP. Например, фильтр, возвращающий только те контактные объекты, которые представляют телефоны общего пользования в городе Редмонд, выглядит следующим образом:</p>
<p>-LDAPFilter &quot;l=Redmond&quot;</p>
<p>В предыдущем примере символ &quot;l&quot; (строчная буква L) — это атрибут Active Directory (расположение), символ &quot;=&quot; — это оператор сравнения (равно), а слово &quot;Redmond&quot; — это значение фильтра.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Позволяет вернуть контактные объекты из определенного подразделения Active Directory. Параметр OU возвращает данные как из указанного подразделения, так и из его дочерних подразделений. Например, если подразделение Finance имеет два дочерних подразделения (AccountsPayable и AccountsReceivable), будут возвращены сведения о телефонах общего пользования для каждого из них.</p>
<p>При указании подразделения используйте различающееся имя этого контейнера; например: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>Позволяет ограничить число записей, возвращаемых командой. Например, чтобы вернуть сведения о семи телефонах общего пользования (вне зависимости от того, сколько их имеется в лесу), добавьте параметр ResultSize со значением 7. Имейте в виду, что невозможно указать, сведения о каких именно телефонах должны быть возвращены. Если для параметра ResultSize задано значение 7, но в лесу имеется всего три телефона общего пользования, команда вернет сведения об этих трех телефонах и завершится без ошибки.</p>
<p>В качестве размера результатов может быть указано любое целое число в диапазоне от 0 до 2147483647 включительно. При задании значения &quot;0&quot; команда будет выполняться, но данные возвращаться не будут.</p></td>
</tr>
</tbody>
</table>


## Типы входных данных

Строка. Командлет **Get-CsCommonAreaPhone** принимает переданное по конвейеру строковое значение, представляющее идентификатор телефона общего пользования.

## Типы возвращаемых данных

Командлет **Get-CsCommonAreaPhone** возвращает экземпляры объекта Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact.

## См. также

#### Другие ресурсы

[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)


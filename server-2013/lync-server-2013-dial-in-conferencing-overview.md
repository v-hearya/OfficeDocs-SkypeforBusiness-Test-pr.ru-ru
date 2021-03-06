﻿---
title: Обзор конференц-связи с телефонным подключением в Lync Server 2013
TOCTitle: Обзор конференц-связи с телефонным подключением в Lync Server 2013
ms:assetid: 6e581cef-960a-4730-8b22-91b2129d34e3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398524(v=OCS.15)
ms:contentKeyID: 49310099
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обзор конференц-связи с телефонным подключением в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-30_

Если в организации имеются пользователи, которым необходимо принимать участие в локальных конференциях сервера Lync Server 2013, когда они находятся вне офиса или не имеют доступа к компьютеру, можно развернуть конференц-связь с телефонным подключением, чтобы такие пользователи могли присоединяться к конференциям с помощью телефона телефонной сети общего пользования (ТСОП).

Конференц-связь с телефонным подключением является дополнительным компонентом при развертывании конференц-связи сервера Lync Server 2013. Хотя конференц-связь с телефонным подключением использует некоторые компоненты сервера Lync Server 2013, которые использует также корпоративной голосовой связи, развернуть конференц-связь с телефонным подключением можно даже без развертывания корпоративной голосовой связи.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если требуется конференц-связь с телефонным подключением, то ее необходимо разворачивать в каждом пуле, в котором разворачивается конференц-связь сервера Lync Server 2013. Назначать номера доступа в каждом пуле не обязательно, но функция конференц-связи с телефонным подключением должна быть развернута в каждом пуле. Это требование поддерживает функцию записанного имени, когда пользователь набирает номер доступа в одном пуле для присоединения к конференции сервера Lync Server 2013 в другом пуле.</td>
</tr>
</tbody>
</table>


Должен быть разрешен телефонный доступ к конференциям в политике собраний. По умолчанию приглашение на конференцию с разрешенным телефонным подключением содержит следующие сведения:

  - числовой идентификатор конференции, который определяет конференцию;

  - хотя бы один номер доступа ТСОП;

  - ссылку на параметров доступа к конференц-связи с телефонным подключением, которая содержит полный список номеров доступа со связанными с ними языками, место для создания, сброса или разблокирования персональных идентификационных номеров (ПИН-кодов) и другие сведения, такие как элементы управления двухтональным многочастотным набором (DTMF).

Конференц-связь с телефонным подключением поддерживает как корпоративных, так и анонимных пользователей. Корпоративные пользователи имеют учетные данные Доменные службы Active Directory и учетные записи сервера Lync Server 2013 в своей организации. Анонимные пользователи не имеют корпоративных учетных данных в вашей организации. В контексте конференц-связи с телефонным подключением пользователь в организации федеративного партнера, использующий ТСОП для присоединения к конференции, считается анонимным пользователем. В отличие от других контекстов, в конференц-связи с телефонным подключением проверка подлинности федеративных пользователей не выполняется.

Корпоративные пользователи или ведущие конференции для присоединения к конференции с разрешенным телефонным доступом набирают один номеров доступа к конференции, а затем им предлагается ввести идентификатор конференции. Если ведущий еще не присоединился к конференции, то пользователи могут либо ввести свой добавочный номер в системе объединенных коммуникаций (или полный телефонный номер) и ПИН-код, либо подождать, пока ведущий не допустит их в конференцию. Организаторы собрания могут присоединяться к собранию как ведущие, введя только свой ПИН-код. переднего плана использует комбинацию полного телефонного номера или дополнительного номера и ПИН-кода для однозначного сопоставления корпоративных пользователей с их учетными данными Active Directory. В результате выполняется проверка подлинности и идентификация корпоративных пользователей по имени в конференции. Корпоративные пользователи могут также взять на себя роль в конференции, предопределенную организатором.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если корпоративные пользователи присоединяются к конференции с офисного IP-телефона, с сервера Lync Server 2013 или из оператор Lync 2010, то у них не запрашивается телефонный номер, поскольку они уже прошли проверку подлинности.</td>
</tr>
</tbody>
</table>


Анонимные пользователи, желающие присоединиться к конференции с телефонным подключением, набирают один из номеров доступа к конференции, а затем у них запрашивается идентификатор конференции. Неавторизованным (не прошедшим проверку подлинности) анонимным пользователям также предлагается записать свое имя. Записанные имена идентифицируют неавторизованных пользователей в конференции. Анонимные пользователи не допускаются в конференцию, пока к ней не присоединится хотя бы один авторизованный пользователь или ведущий, и анонимным пользователям нельзя назначать предопределенную роль.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Корпоративные пользователи, которые предпочли не указывать свой телефонный номер и ПИН-код, не являются авторизованными. Им предлагается записать имена, и они будут считаться анонимными пользователями в конференции.</td>
</tr>
</tbody>
</table>


Во время составления расписания организатор собрания может решить ограничить доступ к собранию, сделав его закрытым или заблокированным. В таком случае пользователям с телефонным подключением будет предлагаться пройти проверку подлинности. Если проверка подлинности завершается неудачно, или если пользователи отказываются ее пройти, то такие пользователи перемещаются в "зал ожидания", где ожидают, пока ведущий не решит, принять или отклонить их заявку на участие, или пока срок ожидания не истечет, и они не будут отключены. Пока пользователи с телефонным подключением ожидают решение о допуске к конференции, они прослушивают музыку. После допуска к конференции пользователи с телефонным подключением могут принимать участие в звуковой части конференции и выполнять команды двухтонального многочастотного набора (DTMF) с помощью клавиатуры телефона. Ведущие, подключившиеся к конференции по телефону, могут выполнять команды DTMF, чтобы позволить участникам включать и отключать микрофон, чтобы блокировать и разблокировать конференцию, допускать пользователей из "зала ожидания", а также включать и отключать уведомления о входе и выходе. Ведущие могут также использовать команды DTMF, чтобы допускать всех пользователей из "зала ожидания", в результате чего разрешения собрания изменяются, и к собранию будут допускаться все, кто впоследствии присоединяется. Все участники с телефонным подключением могут использовать команды DTMF, чтобы прослушивать справку или реестр конференции, а также выключать свой звук.

Участники с телефонным подключением (как присоединившиеся из ТСОП, так и другие) прослушивают во время конференции персональные уведомления, например о том, что их звук выключен или включен, что собрание записывается, или что кто-то ожидает в "зале ожидания".

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Участники, присоединившиеся к конференции не путем набора номера, а путем нажатия на соответствующую ссылку, не слышат персональные уведомления.</td>
</tr>
</tbody>
</table>


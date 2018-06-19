﻿---
title: Поиск пользователей Lync Server
TOCTitle: Поиск пользователей Lync Server
ms:assetid: 3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg429701(v=OCS.15)
ms:contentKeyID: 49309500
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Поиск пользователей Lync Server

 

_**Дата изменения раздела:** 2014-05-14_

Вы можете использовать результаты запроса поиска, чтобы настроить пользователей для системы Lync Server 2013. Вы можете осуществлять поиск пользователей по отображаемому имени, имени, фамилии, имени учетной записи диспетчера учетных записей безопасности, SIP-адресу или универсальному коду ресурса (URI).

Вы можете осуществлять поиск пользователей с помощью панели управления Lync Server или оснастки "Пользователи и компьютеры Active Directory". В следующей процедуре описывается использование панели управления Lync Server для поиска пользователей.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При поиске пользователя по его адресу электронной почты в среде с топологией с центральным лесом результаты могут быть неточными. Вместо этого вы можете выполнить поиск пользователей, указав префикс SIP-адреса, например, sip:имя, добавить фильтр поиска и выбрать SIP-адрес с частичным адресом электронной почты, а также воспользоваться командлетом <strong>Get-CSUser</strong>.</td>
</tr>
</tbody>
</table>


## Поиск одного или нескольких пользователей

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Пользователи**.

4.  В поле **Search users** (Поиск пользователей) полностью или частично введите отображаемое имя, имя, фамилию, имя учетной записи диспетчера учетных записей безопасности, SIP-адрес или URI искомой учетной записи пользователя Active Directory, а затем нажмите кнопку **Find** (Найти).

5.  (Необязательно) Задайте дополнительные критерии поиска, чтобы сократить количество результатов:
    
    1.  Нажмите кнопку со стрелкой развертывания в верхнем правом углу экрана над элементом **Search results** (Результаты поиска) и нажмите кнопку **Add Filter** (Добавить фильтр).
    
    2.  Укажите свойство пользователя, введя его вручную или щелкнув стрелку в раскрывающемся списке и выбрав свойство в этом списке.
    
    3.  В списке **Equal to** (Равно) щелкните элемент **Equal to** (Равно) или **Not equal to** (Не равно).
    
    4.  В текстовом поле введите требуемые условия поиска для фильтрации результатов, а затем нажмите кнопку **Find** (Найти).

6.  Результаты поиска отображаются под элементом **Search Results** (Результаты поиска). Вы можете выбрать любых или всех пользователей в списке и выполнить для них задачи настройки.

## См. также

#### Другие ресурсы

[Просмотр сведений об учетных записях пользователей, разрешенных для Lync Server 2013](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)  
[Подключение и отключение пользователей для Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

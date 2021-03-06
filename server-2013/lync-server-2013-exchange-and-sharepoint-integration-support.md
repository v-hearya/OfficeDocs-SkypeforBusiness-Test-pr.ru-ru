﻿---
title: 'Lync Server 2013: поддержка интеграции Exchange Server и SharePoint'
TOCTitle: Поддержка интеграции Exchange Server и SharePoint
ms:assetid: 72bf8aa5-55b1-4851-8a59-c96bf85d215a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205005(v=OCS.15)
ms:contentKeyID: 49310150
ms.date: 01/20/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Поддержка интеграции Exchange Server и SharePoint в Lync Server 2013

 

_**Дата изменения раздела:** 2017-01-18_

Lync Server 2013 и Lync 2013 могут безопасно и эффективно взаимодействовать с другими приложениями и серверными продуктами, включая Office 2013, Exchange 2013 и SharePoint, если вы интегрируете эти продукты. Интеграция Lync Server 2013 и Office предоставляет пользователям контекстный доступ к возможностям обмена мгновенными сообщениями, расширенным сведениям о присутствии, телефонной и конференц-связи Lync. Пользователи Office могут работать с функциями Lync из клиента обмена сообщениями и совместной работы Outlook 2013 и других программ Office, а также со страницы Microsoft SharePoint Server 2010. Пользователи также могут просматривать записи бесед Lync в папке "Журнал бесед" Outlook. При интеграции с Exchange 2013 или Exchange OnlineLync Server 2013 также поддерживает следующие возможности:

  - единое хранилище контактов, которое позволяет пользователям хранить все контактные данные в Exchange 2013 или Exchange Online так, что они доступны глобально в Lync 2013, Exchange, Outlook и Outlook Web App;

  - журнал бесед и журнал веб-конференций, хранящиеся в пользовательских папках Exchange;

  - архивированное содержимое из Lync, например, мгновенные сообщения и собрания, могут храниться в Exchange.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 поддерживает интеграцию с предыдущими версиями Microsoft Exchange Server и SharePoint, однако при этом доступны не все функциональные возможности, например, невозможна интеграция хранилища архивации с Microsoft Exchange.<br />
Если вы выполняете миграцию пользователей в Exchange 2013, вы можете одновременно использовать хранилище Exchange и хранилище Lync Server в качестве временного решения в процессе миграции. Постоянное использование обоих хранилищ (Exchange и Lync Server) не поддерживается.</td>
</tr>
</tbody>
</table>


Интеграция Lync Server 2013 с Exchange 2013 и SharePoint Server требует проверки подлинности между серверами Lync Server 2013, Microsoft Exchange Server и SharePoint Server. Lync Server 2013 поддерживает протокол OAuth для межсерверной проверки подлинности и авторизации. Для межсерверной проверки подлинности между двумя локальными серверами Майкрософт нет необходимости использовать сторонний сервер маркеров. Lync Server 2013, Exchange 2013 и SharePoint имеют встроенный сервер маркеров, который можно использовать для проверки подлинности между этими продуктами. Например, сервер Lync Server 2013 может самостоятельно выпустить и подписать маркер безопасности, а затем использовать его при взаимодействии с Exchange 2013. В этом случае не нужно использовать сторонний сервер маркеров.

Lync Server 2013 поддерживает два сценария межсерверной проверки подлинности между следующими компонентами:

  - локальная установка Lync Server 2013 и локальная установка Exchange 2013 или SharePoint Server;

  - пара компонентов Office (например, Microsoft Exchange 365 и Microsoft Lync Server 365 или Microsoft Lync Server 365 и Microsoft SharePoint 365).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Межсерверная проверка подлинности между локальным сервером и компонентом Office 365 не поддерживается в этом выпуске Lync Server 2013. Помимо прочего, это означает, что вы не можете настроить межсерверную проверку подлинности между локальной установкой Lync Server 2013 и Microsoft Exchange 365.</td>
</tr>
</tbody>
</table>


Подробные сведения о межсерверной проверке подлинности см. в разделе [Управление проверкой подлинности между серверами (OAuth) и партнерскими приложениями в Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) в документации по развертыванию или документации по эксплуатации.


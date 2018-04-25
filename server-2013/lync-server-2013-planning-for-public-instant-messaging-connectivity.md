﻿---
title: Планирование соединения для общедоступных служб обмена мгновенными сообщениями в Lync Server 2013
TOCTitle: Планирование соединения для общедоступных служб обмена мгновенными сообщениями в Lync Server 2013
ms:assetid: e75e8884-05c7-414a-8014-bc9aa8126fb7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205349(v=OCS.15)
ms:contentKeyID: 49311496
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Планирование соединения для общедоступных служб обмена мгновенными сообщениями в Lync Server 2013

 

_**Дата изменения раздела:** 2017-03-09_

Возможность подключения к общедоступным службам обмена мгновенными сообщениями — это класс федерации. Она настраивается для того, чтобы позволить внутренним и внешним пользователям системы Lync Server 2013 добавлять следующие контакты:

  - Контакты Messenger

  - Контакты Yahoo\!

  - Контакты America Online (AOL)

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>С 1 сентября 2012 г. прекращена продажа лицензий пользовательских подписок на подключение к общедоступным службам обмена мгновенными сообщениями Microsoft Lync (PIC USL) по новым или продляемым соглашениям. Клиенты с активными лицензиями смогут продолжать использование федерации с Yahoo! Messenger до отключения службы. Поддержка служб AOL и Yahoo! завершается в июне 2014 г. Дополнительные сведения см. в статье <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Поддержка подключения к общедоступным службам обмена мгновенными сообщениями в Lync Server 2013</a>.</p></li>
<li><p>Лицензия PIC USL — это помесячная лицензия подписки на пользователя, которая требуется для федерации Lync Server или Office Communications Server с Yahoo! Messenger. Возможность Майкрософт предоставлять эту службу зависит от поддержки со стороны Yahoo!, необходимое соглашение для которой не будет продлено.</p></li>
<li><p>Как никогда ранее, Lync является мощным средством для связи организаций и отдельных людей по всему миру. Федерация с Windows Live Messenger не требует дополнительных лицензий на пользователя или устройство помимо клиентской лицензии Lync Standard. Федерация со Skype будет добавлена в этот список, позволяя пользователям Lync связываться с сотнями миллионов людей с помощью мгновенных сообщений и голосовой связи.</p></li>
</ul></td>
</tr>
</tbody>
</table>


При планировании для этого класса федерации необходимо учитывать следующее:

  - Кроме обмена мгновенными сообщениями, пользователи Windows Live Messenger могут осуществлять одноранговую аудио или видеосвязь с пользователямиLync Server 2013. Пограничные сервер должны соответствовать определенным требованиям к портам и протоколам. Дополнительные сведения см. в разделе [Определение требований к внешнему брандмауэру аудио- и видеосвязи и портам для Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md).

  - Обмен мгновенными сообщениями Yahoo не имеет каких-либо уникальных требований, отличных от тех, которые обычно применяются при планировании и развертывании типичной пограничной сервер, предоставляющей федерацию.

  - America Online требует, чтобы сертификат сервер, назначенный доступа, содержал EKU клиента.

## Содержание

  - [Сводка о сертификации — подключение к общедоступным системам обмена мгновенными сообщениями](lync-server-2013-certificate-summary-public-instant-messaging-connectivity.md)

  - [Сводка по портам — подключение к общедоступным системам обмена мгновенными сообщениями](lync-server-2013-port-summary-public-instant-messaging-connectivity.md)

  - [Сводка по DNS — подключение к общедоступным системам обмена мгновенными сообщениями](https://technet.microsoft.com/ru-ru/library/jj618375\(v=ocs.15\))

﻿---
title: Сводка по DNS — федерация XMPP
TOCTitle: Сводка по DNS — федерация XMPP
ms:assetid: 0f720a2a-8ab5-43cc-882a-ab595ed3cec7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ618368(v=OCS.15)
ms:contentKeyID: 49308956
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по DNS — федерация XMPP

 

_**Дата изменения раздела:** 2015-03-09_

Чтобы настроить для развертывания расширяемый протокол обмена сообщениями и контроля присутствия (XMPP), создают две записи службы доменных имен (DNS) на внешнем DNS-сервере, который разрешает записи в доступа вашего сервер или пул.

## Сводка по DNS для расширяемого протокола XMPP


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Расположение/ТИП/порт</th>
<th>Полное доменное имя</th>
<th>IP-адрес/запись узла полного доменного имени</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешний DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>Внешний интерфейс прокси-сервера XMPP для доступа или пул. Повторите требуемое число раз для всех внутренних SIP-доменов с пользователями, обладающими возможностями Lync, где разрешен контакт с XMPP-контактами через конфигурацию политики внешнего доступа, реализуемую через глобальную политику, политику сайта, на котором находится пользователь или пользовательскую политику, применяемую к пользователю, обладающему возможностями Lync. Разрешенный XMPP-домен должен быть также настроен в политике федеративных партнеров XMPP. Дополнительные сведения, см. в статьях, указанных в разделе <strong>См. также</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Внешняя DNS/A</p></td>
<td><p>xmpp.contoso.com (пример)</p></td>
<td><p>IP-адрес доступа в сервер или пул, где размещен прокси-сервер XMPP</p></td>
<td><p>Указывает на доступа или пул, где размещен прокси-сервер XMPP. Как правило, созданная запись SRV указывает на эту запись узла (A или AAAA).</p></td>
</tr>
</tbody>
</table>


## См. также

#### Задачи

[Настройка федерации XMPP в Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  

#### Концепции

[Определение требований DNS для Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

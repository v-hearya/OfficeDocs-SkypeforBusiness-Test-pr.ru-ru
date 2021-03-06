﻿---
title: 'Lync Server 2013: сводка по сертификатам — единственный директор'
TOCTitle: Сводка по сертификатам — единственный директор
ms:assetid: 1b769a76-cbf3-46e9-a955-f6cde5faff93
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204720(v=OCS.15)
ms:contentKeyID: 49309105
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по сертификатам — единственный директор в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Для отдельного Директора требуется сертификат по умолчанию, имеющий имя субъекта и альтернативные имена субъектов для служб, которые может принимать Директор. Кроме того, существует сертификат маркера OAuth для проверки подлинности «сервер-сервер».

### Сертификаты для Директора

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Компонент</th>
<th>Имя субъекта (SN)</th>
<th>Дополнительные имена субъектов (SAN)</th>
<th>Комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>По умолчанию</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>dir01.contoso.net</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>lyncdiscoverinternal.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(Дополнительно) *.contoso.com</p></td>
<td><p>Сертификаты Директор могут быть запрошены как во внутреннем центре сертификации, так и во внешнем центре сертификации.</p>
<p>Директор отвечает на запросы обратного прокси-сервера в сети периметра или сервер. Внутренние клиенты не будут использовать Директор.</p>
<p>Или групповая запись для простых URL-адресов</p></td>
</tr>
<tr class="even">
<td><p>OAuthTokenIssuer</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Без записи</p></td>
<td><div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Обратите внимание, что минимальная длина ключа равна 1024, однако может возникнуть предупреждение, что рекомендуемая минимальная длина равна 2048 битам.</td>
</tr>
</tbody>
</table>

</div>
<p>Сертификат OAuthTokenIssuer является сертификатом, который служит исключительно для проверки подлинности серверов в крупных средах. Его можно запросить у внутреннего или внешнего центра сертификации. Сертификат является обязательным.</p>
<p></p></td>
</tr>
</tbody>
</table>


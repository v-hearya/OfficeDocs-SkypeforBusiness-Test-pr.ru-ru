﻿---
title: 'Lync Server 2013: поддерживаемое выровненное размещение серверов для пограничных компонентов'
TOCTitle: Поддерживаемое выровненное размещение серверов для пограничных компонентов
ms:assetid: 435c4dd8-36af-4b71-9b88-3ffcf0fc5c65
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425934(v=OCS.15)
ms:contentKeyID: 49309597
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Поддерживаемое выровненное размещение серверов для пограничных компонентов в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-08_

Служба пограничного доступа, служб веб-конференций пограничного сервера, пограничная служба аудио- и видеоданных и служба прокси-сервера XMPP совместно размещаются в сервер. Следующие серверы предоставляют функции, необходимые для доступа внешних пользователей, и их следует развернуть как выделенные серверы:

  - сервер

  - Директор (необязательно);

  - Сертификат обратного прокси-сервера

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Обратный прокси-сервер не должен быть выделенным, если обслуживается только Lync Server 2013. Например, можно предоставить службы для публикации веб-служб Lync Server и одновременно предоставить опубликованный веб-сайт для другого сайта, который совсем не зависит от Lync Server. Если у вас уже есть обратный прокси-сервер в сети периметра для поддержки других служб, его можно использовать для Lync Server 2013.</td>
</tr>
</tbody>
</table>

﻿---
title: Настройка добавочных номеров для парковки вызовов
TOCTitle: Настройка добавочных номеров для парковки вызовов
ms:assetid: fbf97624-9587-42a6-b276-1b69c574a74d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182611(v=OCS.15)
ms:contentKeyID: 49311767
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка добавочных номеров для парковки вызовов

 

_**Дата изменения раздела:** 2012-09-10_

Приложение приостановки вызовов использует добавочные номера в таблице орбит Приостановка вызовов для парковки вызовов. Вам необходимо настроить таблицу орбит Приостановка вызовов с диапазонами добавочных номеров, зарезервированных вашей организацией для запаркованных вызовов. Эти добавочные номера должны быть виртуальными (то есть не иметь назначенного пользователя или назначенный телефон). Каждый пул Lync Server, в котором развернуто и настроено приложение приостановки вызовов, может иметь один или несколько диапазонов орбит. Диапазоны орбит должны быть уникальными в рамках всего развертывания Lync Server.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед использованием Приостановка вызовов следует установить флажок <strong>Разрешить парковку вызовов</strong> в политике голосовой связи. По умолчанию данный параметр не выбран.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Создание или изменение диапазона орбит для парковки вызовов в Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

  - [Удаление диапазона орбит для парковки вызовов в Lync Server 2013](lync-server-2013-delete-a-call-park-orbit-range.md)


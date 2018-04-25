﻿---
title: Настройка корпоративной голосовой связи в Lync Server 2013
TOCTitle: Настройка корпоративной голосовой связи в Lync Server 2013
ms:assetid: 7df179fa-d3a2-4b23-a433-b750aedf980b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ994041(v=OCS.15)
ms:contentKeyID: 52058254
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка корпоративной голосовой связи в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Для развертывания корпоративной голосовой связи необходимо выполнить следующие действия:

  - создать линию связи;

  - определить политику голосовой связи;

  - определить маршрут голосовых вызовов;

  - включить корпоративную голосовую связь для пользователей.

## Создание линии связи

В развертывании корпоративной голосовой связи необходимо определить линию связи. Для маршрутизации на основе расположения нужно создать конфигурацию для каждой линии связи. Используйте Lync Serverтопологий, чтобы определить линии связи, а также команду Lync ServerWindows PowerShell, New-CsTrunkConfiguration или управления Lync Server, чтобы определить соответствующие конфигурации линий связи. Подробнее о том, как включить в этих конфигурациях маршрутизацию на основе расположения, см. в разделе "Включение маршрутизации на основе расположения" статьи [Включение маршрутизации на основе расположения в Lync Server 2013](lync-server-2013-enabling-location-based-routing.md). Для этого примера в приведенной ниже таблице показаны линии связи, использованные в этом сценарии.

Подробнее см. в статье [Определение дополнительных магистралей в постороителе топологий в Lync Server 2013](lync-server-2013-define-additional-trunks-in-topology-builder.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя линии связи</th>
<th>Тип системы</th>
<th>Имя</th>
<th>Расположение</th>
<th>посредник</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Линия связи 1 DEL-GW</p></td>
<td><p>Шлюз ТСОП</p></td>
<td><p>DEL-GW</p></td>
<td><p>Дели</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Линия связи 2 HYD-GW</p></td>
<td><p>Шлюз ТСОП</p></td>
<td><p>HYD-GW</p></td>
<td><p>Хайдарабад</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="odd">
<td><p>Линия связи 3 DEL-PBX</p></td>
<td><p>УАТС</p></td>
<td><p>DEL-PBX</p></td>
<td><p>Дели</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Линия связи 4 HYD-PBX</p></td>
<td><p>УАТС</p></td>
<td><p>HYD-PBX</p></td>
<td><p>Хайдарабад</p></td>
<td><p>MS1</p></td>
</tr>
</tbody>
</table>



## Определение голосовых политик

Для развертывания корпоративной голосовой связи необходимо определить политики голосовой связи. Определите такую политику, чтобы применить ограничения маршрутизации на основе расположения к подмножеству пользователей (если требуется). Для примера в приведенной ниже таблице показаны политики голосовой связи, использованные в этом сценарии. В таблицу для наглядности включены только параметры, относящиеся к маршрутизации на основе расположения.

Подробнее см. в статье [Настройка политик голосовой связи и записей использования ТСОП для авторизации функций звонков и предоставления привилегий в Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Политика голосовой связи 1</th>
<th>Политика голосовой связи 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Идентификатор политики голосовой связи</p></td>
<td><p>Политика голосовой связи в Дели</p></td>
<td><p>Политика голосовой связи в Хайдарабаде</p></td>
</tr>
<tr class="even">
<td><p>Использование ТСОП</p></td>
<td><p>Использование в Дели, использование УАТС Дели, использование УАТС Хайд</p></td>
<td><p>Использование в Хайдарабаде, использование УАТС Хайд, использование УАТС Дели</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>Недопустимо</p></td>
<td><p>Недопустимо</p></td>
</tr>
</tbody>
</table>



## Определение маршрута голосовой связи

Для развертывания корпоративной голосовой связи необходимо определить маршрут голосовой связи. Для примера в следующей таблице показаны маршруты голосовой связи, использованные в этом сценарии. В таблицу для наглядности включены только параметры, относящиеся к маршрутизации на основе расположения.

Подробнее см. в статье [Настройка маршрутов голосовой связи для исходящих звонков в Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Маршрут голосовой связи 1</th>
<th>Маршрут голосовой связи 2</th>
<th>Маршрут голосовой связи 3</th>
<th>Маршрут голосовой связи 4</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Имя</p></td>
<td><p>Маршрут Дели</p></td>
<td><p>Маршрут Хайдарабада</p></td>
<td><p>Маршрут УАТС Дели</p></td>
<td><p>Маршрут УАТС Хайд</p></td>
</tr>
<tr class="even">
<td><p>Использования ТСОП</p></td>
<td><p>Использование в Дели</p></td>
<td><p>Использование в Хайдарабаде</p></td>
<td><p>Использование УАТС Дели</p></td>
<td><p>Использование УАТС Хайд</p></td>
</tr>
<tr class="odd">
<td><p>Линия связи</p></td>
<td><p>Линия связи 1 DEL-GW</p></td>
<td><p>Линия связи 2 HYD-GW</p></td>
<td><p>Линия связи 3 DEL-УАТС</p></td>
<td><p>Линия связи 4 HYD-УАТС</p></td>
</tr>
</tbody>
</table>



## Включение корпоративной голосовой связи для пользователей

Включите корпоративной голосовой связи для пользователей и назначьте им ранее определенную политику голосовой связи. Для примера в приведенной ниже таблице показано назначение, используемое в этом сценарии. В таблицу для наглядности включены только параметры, относящиеся к маршрутизации на основе расположения.

Подробнее см. в статье [Включение пользователей для корпоративной голосовой связи в Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Пользователи, расположенные в Дели</th>
<th>Пользователи, расположенные в Хайдарабаде</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Связанная политика голосовой связи</p></td>
<td><p>Политика голосовой связи в Дели</p></td>
<td><p>Политика голосовой связи в Хайдарабаде</p></td>
</tr>
<tr class="even">
<td><p>Пример пользователей</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
</tbody>
</table>



## См. также

#### Другие ресурсы

[Настройка маршрутизации на основе расположения в Lync Server 2013](lync-server-2013-configuring-location-based-routing.md)

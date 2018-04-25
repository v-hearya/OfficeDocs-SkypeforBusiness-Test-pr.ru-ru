﻿---
title: 'Lync Server 2013: сводка по DNS — обратный прокси-сервер'
TOCTitle: Сводка по DNS — обратный прокси-сервер
ms:assetid: 3073affa-4d92-4453-9974-3a82ca0c6445
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204781(v=OCS.15)
ms:contentKeyID: 49309343
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по DNS — обратный прокси-сервер в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Два сетевых адаптера на обратном прокси-сервере можно настроить следующим образом:

## Требования к сетевым адаптерам обратного прокси-сервера

  - **Сетевой адаптер 1 (внутренний интерфейс)** (пример)
    
    Назначенный внутренний интерфейс с 172.25.33.40.
    
    Шлюз по умолчанию не определен.
    
    Убедитесь, что существует маршрут от сети с внутренним интерфейсом обратного прокси-сервера до сетей, которые содержат серверы пула переднего планаLync Server (например, от 172.25.33.0 до 192.168.10.0).

  - **Сетевой адаптер 2 (внешний интерфейс)** (пример)
    
    Как минимум один общедоступный IP-адрес назначен данному сетевому адаптеру.
    
    Шлюз определен так, что он указывает на маршрутизатор или интегрированный брандмауэр во внешнем периметре. (10.45.16.1 в примерах)

### Записи DNS, необходимые для обратного прокси-сервера

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Местоположение/тип/порт</th>
<th>Полное доменное имя</th>
<th>IP-адрес</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>Назначенный прослушиватель для внешних опубликованных ресурсов</p></td>
<td><p>Внешние веб-службы из внутреннего развертывания. Могут быть определены и созданы дополнительные записи для всех пулов и отдельных серверов для любого SIP-домена, который будет использовать это обратный прокси-сервер и на котором определены внешние веб-службы.</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>webdirext.contoso.com</p></td>
<td><p>Назначенный прослушиватель для внешних опубликованных ресурсов</p></td>
<td><p>Внешние веб-службы для пулов Директор или Директор в развертывании. Вы можете определить столько Директор, сколько существует отдельных Директор, некоторые из которых могут быть связаны с другими SIP-доменами.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Определение записей DNS и публикация Директоров не является решением, связанным с пулом переднего плана или Директором. Необходимо определить и опубликовать внешние веб-службы Директора и пула переднего плана, если вы используете Директоры. Определенные типы трафика (для проверки подлинности и других целей) сначала отправляются на Директор, если это задано в топологии.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>dialin.contoso.com</p></td>
<td><p>Назначенный прослушиватель для внешних опубликованных ресурсов</p></td>
<td><p>Ресурсы конференц-связи с телефонным подключением, опубликованные внешне</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>meet.contoso.com</p></td>
<td><p>Назначенный прослушиватель для внешних опубликованных ресурсов</p></td>
<td><p>Конференции, опубликованные внешне</p></td>
</tr>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>officewebapps01.contoso.com</p></td>
<td><p>Назначенный прослушиватель для Сервер Office Web Apps</p></td>
<td><p>Сервер Office Web Apps развернут внутри или в сети периметра и опубликован для внешнего доступа клиентов</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>lyncdiscover.contoso.com</p></td>
<td><p>Назначенный прослушиватель для внешних опубликованных ресурсов</p></td>
<td><p>Внешняя запись обнаружения Lync для внешне опубликованного автообнаружения, включая мобильность, Microsoft Lync Web App и веб-приложение планировщика</p></td>
</tr>
</tbody>
</table>

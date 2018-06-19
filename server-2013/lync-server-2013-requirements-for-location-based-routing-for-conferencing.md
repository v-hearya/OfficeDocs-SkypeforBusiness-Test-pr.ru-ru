﻿---
title: Требования к маршрутизации на основе расположения для конференц-связи
TOCTitle: Требования к маршрутизации на основе расположения для конференц-связи
ms:assetid: 766d9286-2c34-4faf-bb3e-f0ca478a70cf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn362806(v=OCS.15)
ms:contentKeyID: 56270563
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Требования к маршрутизации на основе расположения для конференц-связи

 

_**Дата изменения раздела:** 2016-12-08_

Ниже приведены требования, необходимые для установки и настройки приложения конференц-связи с маршрутизацией на основе расположения.

  - Накопительный пакет обновления 2 для Lync Server 2013 должен быть развернут на всех серверах и в пулах топологии.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если на сервере или в пуле Lync в топологии не установлен накопительный пакет обновления 2 (или более поздней версии) для Lync Server 2013, то маршрутизация на основе расположения для собраний Lync не гарантируется.</td>
</tr>
</tbody>
</table>


  - Маршрутизация на основе расположения Lync Server 2013  — необходимое условие для работы приложения конференц-связи с маршрутизацией на основе расположения. Подробнее о настройке маршрутизации на основе расположения Lync Server 2013 см. в статье [Настройка маршрутизации на основе расположения](lync-server-2013-configuring-location-based-routing.md).

  - Требования к приложению конференц-связи с маршрутизацией на основе расположения такие же, как и для маршрутизации на основе расположения Lync Server 2013. Подробнее см. в статье [Планирование маршрутизации на основе расположения](lync-server-2013-planning-for-location-based-routing.md).

## Поддерживаемые серверы

Для приложения конференц-связи с маршрутизацией на основе расположения необходимо, чтобы во всех интерфейсных пулах и на всех серверах с выпуском Standard Edition в топологии был развернут накопительный пакет обновления 2 для Lync Server 2013. Если он не установлен на некоторых серверах Lync в топологии, к собраниям Lync и переводам вызовов с консультацией не могут полностью применяться ограничения маршрутизации на основе расположения.

В указанной ниже таблице приведено сочетание ролей серверов и версий, поддерживающих маршрутизацию на основе расположения.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Версия интерфейсного пула</p></td>
<td><p>Версия cервера-посредника</p></td>
<td><p>Поддерживается</p></td>
</tr>
<tr class="even">
<td><p>Накопительный пакет обновления 2 для Lync Server 2013</p></td>
<td><p>Накопительный пакет обновления 2 для Lync Server 2013</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Накопительный пакет обновления 2 для Lync Server 2013</p></td>
<td><p>Накопительный пакет обновления 1 для Lync Server 2013</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Накопительный пакет обновления 2 для Lync Server 2013</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Накопительный пакет обновления 2 для Lync Server 2013</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Накопительный пакет обновления 1 для Lync Server 2013</p></td>
<td><p>Любая</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010</p></td>
<td><p>Любая</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>Любая</p></td>
<td><p>Нет</p></td>
</tr>
</tbody>
</table>


## Поддерживаемые клиенты

Клиенты Lync, которые поддерживают маршрутизацию на основе расположения для собраний Lync, — те же клиенты, что поддерживают маршрутизацию на основе расположения Lync Server 2013. Подробнее см. в статье [Поддержка маршрутизации на основе расположения клиентами и серверами](lync-server-2013-client-and-server-support-for-location-based-routing.md).

## Требования к cерверу-посреднику для перевода вызовов с консультацией

Для приложения конференц-связи с маршрутизацией на основе расположения требуется развертывание автономного сервера-посредника. Это необходимо для соблюдения ограничений маршрутизации на основе расположения для перевода вызовов с консультацией.

Чтобы обеспечить маршрутизацию на основе расположения для перевода вызовов с консультацией, сервер-посредник должен быть связан только с одним узлом сервера-посредника (например, УАТС, шлюзом SIP и пр.) в областях сети, где требуется маршрутизация на основе расположения. Если в одной и той же области сети развернуты дополнительные узлы сервера-посредника, их необходимо связать с другим сервером-посредником. Подробное описание этого требования приведено ниже.

  - Один сервер-посредник на несколько узлов сервера-посредника. Когда передача вызова с консультацией направляется на узел сервера-посредника через сервер-посредник, на котором настроены несколько магистралей SIP для нескольких узлов (например, УАТС и шлюзов), то передача вызовов с консультацией блокируется во избежание обхода платных звонков по ТСОП, если такая передача разрешена только по некоторым из магистралей SIP.
    
    Например, если один сервер-посредник обслуживает и узел сервера-посредника шлюза ТСОП, и узел сервера-посредника УАТС, то будет наблюдаться следующее:
    
      - при попытке пользователя Lync с данного сайта (например, сайта 1) перевести вызов с конечной точкой ТСОП пользователю Lync с другого сайта (например, сайта 2) путем передачи вызова с консультацией звонок будет запрещен во избежание обхода платных звонков по ТСОП;
    
      - при попытке пользователя Lync с данного сайта (сайта 1) перевести вызов с использованием конечной точки УАТС на том же сайте (сайте 1) пользователю Lync с другого сайта (сайта 2) путем передачи вызова с консультацией звонок будет запрещен, даже если он не несет потенциальной опасности обхода платных звонков по ТСОП.

  - Отдельные серверы-посредники для каждого узла сервера-посредника
    
    Когда передача вызова с консультацией ориентирована на узел сервера-посредника, она оценивается по отношению к одиночному узлу сервера-посредника, который обслуживается сервером-посредником. Вызов будет запрещен или разрешен, исходя из возможной попытки обхода платных звонков по ТСОП, независимо от остальных узлов сервера-посредника на сайте, так как они обслуживаются отдельным сервером-посредником.
    
    Например, в случае отдельных серверов-посредников, обслуживающих узел сервера-посредника шлюза ТСОП и узел сервера-посредника УАТС, будет наблюдаться следующее:
    
      - при попытке пользователя Lync с данного сайта (например, сайта 1) перевести вызов с конечной точкой ТСОП пользователю Lync с другого сайта (например, сайта 2) путем передачи вызова с консультацией звонок будет запрещен во избежание обхода платных звонков по ТСОП;
    
      - при попытке пользователя Lync с данного сайта (сайта 1) перевести вызов с использованием конечной точки УАТС на том же сайте (сайте 1) пользователю Lync с другого сайта (сайта 2) путем передачи вызова с консультацией звонок будет разрешен, так как он не несет потенциальной опасности обхода платных звонков по ТСОП.

## Возможности, не поддерживаемые приложением конференц-связи с маршрутизацией на основе расположения

Приложение конференц-связи с маршрутизацией на основе расположения не поддерживает указанные ниже возможности.

  - Конференц-связь с телефонным подключением. Маршрутизация на основе расположения не может быть реализована для конференц-связи с телефонным подключением. Любой запрос на телефонное подключение к данной конференции не будет ограничен маршрутизацией на основе расположения, даже если организатор конференции — пользователь Lync, которому разрешена маршрутизация на основе расположения.

  - Рекомендуется не предоставлять номера доступа к конференц-связи в регионах, где должны соблюдаться ограничения маршрутизации на основе расположения.

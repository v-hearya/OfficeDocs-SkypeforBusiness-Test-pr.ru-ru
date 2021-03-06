﻿---
title: 'Lync Server 2013: планирование устойчивости голосовой связи для центрального сайта'
TOCTitle: Планирование устойчивости голосовой связи для центрального сайта
ms:assetid: 52dd0c3e-cd3c-44cf-bef5-8c49ff5e4c7a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398347(v=OCS.15)
ms:contentKeyID: 49309765
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Планирование устойчивости голосовой связи для центрального сайта в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Все чаще у предприятий появляется много сайтов, распределенных по всему миру. Поддержка экстренных служб, доступ к службе технической поддержки и возможность выполнения важных бизнес-задач в случае выхода из строя центрального сайта является неотъемлемой частью любого решения по устойчивости корпоративной голосовой связи. Когда центральный сайт выходит из строя, должны выполняться следующие условия.

  - Должна обеспечиваться отработка отказа голосовой связи.

  - Пользователи, обычно регистрирующиеся в пуле серверов переднего плана на центральном сайте, должны иметь возможность регистрации в другом пуле серверов переднего плана. Это можно сделать путем создания нескольких записей DNS SRV, каждая из которых разрешается в пул Директоров или в пул серверов переднего плана на каждом центральном сайте. Можно настроить приоритет и вес записей SRV, чтобы пользователи, обслуживающиеся на центральном сайте, получали соответствующий пул Директор и пул серверов переднего плана перед указанными в других записях SRV.

  - Входящие и исходящие вызовы пользователей, расположенных на других сайтах, должны перенаправляться в ТСОП.

В этой статье описывается рекомендуемое решение для защиты устойчивости центрального сайта голосовой связи.

## Архитектура и топология

Для планирования устойчивости голосовой связи на центральном сайте необходимо базовое понимание центральной роли, которую играет регистратор сервера Lync Server 2013 в поддержке отработки отказа голосовой связи. Регистратор Lync Server – это новая роль сервера, которая позволяет выполнять регистрацию и проверку подлинности клиентов, а также предоставляет службы маршрутизации. Регистратор располагается вместе с другими компонентами на сервере Сервер Standard Edition, сервере переднего плана, сервере Директор или в устройстве для обеспечения связи в филиалах. Пул регистратора состоит из служб регистратора, работающих в пуле серверов переднего плана и размещенных на том же сайте. Пул серверов переднего плана должен быть с балансировкой нагрузки. Рекомендуется балансировка нагрузки на DNS, но допустима и аппаратная балансировка нагрузки. Клиент Lync обнаруживает пул серверов переднего плана с помощью следующего механизма обнаружения.

1.  SRV-запись DNS

2.  Веб-служба автоматического обнаружения (новая в Lync Server 2013)

3.  Параметр DHCP 120

После подключения клиента Lync к пулу переднего плана он направляется балансировщиком нагрузки на один из переднего плана пула. В свою очередь переднего плана перенаправляет клиента на предпочтительный регистратор в пуле.

Каждый пользователь с поддержкой корпоративной голосовой связи назначается конкретному пулу регистратора, который становится основным пулом регистратора этого пользователя. На конкретном сайте сотни или тысячи пользователей обычно совместно используют один основной пул регистратора. Учитывая потребление ресурсов центрального сайта всеми пользователями сайтов филиалов, функции присутствия, конференц-связи или отработки отказа которых зависят от центрального сайта, мы рекомендуем рассматривать каждого пользователя сайта филиала, как если бы он был зарегистрирован на центральном сайте. В настоящее время не существует ограничений на количество пользователей сайта филиала, включая пользователей, зарегистрированных с помощью устройства для обеспечения связи в филиалах.

Для обеспечения устойчивости голосовой связи в случае сбоя центрального сайта основной пул регистратора должен иметь один назначенный резервный пул регистратора, расположенный на другом сайте. Этот резервный пул можно настроить с помощью параметров устойчивости построителя топологий. Если существует устойчивая связь WAN между этими двумя сайтами, то пользователи, чей основной пул регистратора стал недоступен, автоматически перенаправляются в резервный пул регистратора.

Следующие действия описывают процесс обнаружения и регистрации клиента.

1.  Клиент обнаруживает Lync Server с помощью записей DNS SRV. В сервере Lync Server 2013 записи DNS SRV можно настроить таким образом, чтобы они возвращали в ответ на запрос DNS SRV несколько полных доменных имен. Например, если предприятие Contoso имеет три центральных сайта (в Северной Америке, в Европе и в Азиатско-Тихоокеанском регионе), и пул Директор существует на каждом центральном сайте, то записи DNS SRV могут указывать на полное доменное имя пула Директор в каждом из этих трех расположений. Пока пул Директор в одном из расположений доступен, клиент может подключиться к серверу Lync Server первого прыжка.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Использование пула Директоров не является обязательным. Вместо него можно использовать пул серверов переднего плана.</td>
    </tr>
    </tbody>
    </table>


2.  Пул Директоров информирует клиента Lync об основном и резервном пуле регистратора пользователя.

3.  Клиент Lync сначала пытается подключиться к основному пулу регистратора пользователя. Если основной пул регистратора доступен, то регистратор принимает регистрацию. Если основной пул регистратора недоступен, то клиент Lync пытается подключиться к резервному пулу регистратора. Если резервный пул регистратора доступен и определяет, что основной пул регистратора недоступен (обнаруживая отсутствие пульса для указанного интервала отработки отказа), то этот резервный пул регистратора принимает регистрацию пользователя. После того как резервный пул регистратора обнаружит, что основной регистратор снова доступен, он перенаправляет клиентов Lync в их основной пул.

На следующем рисунке показана рекомендуемая топология для обеспечения устойчивости центрального сайта. На этом рисунке два сайта соединяются устойчивой связью WAN. Если центральный сайт становится недоступен, то назначенные этому пулу пользователи перенаправляются на резервный сайт для регистрации.

**Рекомендуемая топология для устойчивости центрального сайта**

![Топология центрального сайта, обеспечивающего надежность голосовой связи](images/Gg398347.19ea3e74-8a5c-488c-a34e-fc180ab9a50a(OCS.15).jpg "Топология центрального сайта, обеспечивающего надежность голосовой связи")

## Требования и рекомендации

Следующие требования и рекомендации для реализации устойчивости голосовой связи на центральном сайте подходят для большинства организаций.

  - Сайты, на которых размещаются основной и резервный пулы регистратора, должны быть связаны устойчивой связью WAN.

  - На каждом центральном сайте должен быть пул регистратора, состоящий из одного или нескольких регистраторов.

  - Каждый пул регистратора должен иметь балансировку нагрузки с использованием балансировки нагрузки DNS, аппаратную балансировку нагрузки или обе . Подробные сведения о планировании конфигурации балансировки нагрузки см. в статье [Требования к балансировке нагрузки в Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

  - Каждый пользователь должен быть назначен в основной пул регистратора с помощью командлета **set-CsUser** командной консоли Командная консоль Lync Server или с помощью панели управления Lync Server.

  - Основной пул регистратора должен иметь один резервный пул регистратора, расположенный на другом центральном сайте.

  - Основной пул регистратора должен быть настроен для отработки отказа в резервный пул регистратора. По умолчанию задана отработка отказа основного пула регистратора в резервный пул через 300 секунд. Этот интервал можно изменить с помощью построителя топологий сервера Lync Server 2013.

  - Настройте маршрут отработки отказа, как описано в разделе [Настройка маршрута отработки отказа в Lync Server 2013](lync-server-2013-configuring-a-failover-route.md) документации по планированию. При настройке маршрута укажите шлюз, расположенный на другом сайте, чем шлюз, указанный в основном маршруте.

  - Если центральный сайт, на котором размещается основной сервер управления, возможно, вышел из строя на длительное время, то придется переустановить средства управления на резервном сайте, иначе не будет возможности изменить какие-либо параметры управления.

## Зависимости

В плане обеспечения устойчивости голосовой связи Lync Server зависит от следующих компонентов инфраструктуры и программного обеспечения.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Компонент</strong></p></td>
<td><p><strong>Функция</strong></p></td>
</tr>
<tr class="even">
<td><p>DNS</p></td>
<td><p>Разрешение записей SRV и A для сервера и для возможности подключения клиента к серверу</p></td>
</tr>
<tr class="odd">
<td><p>Exchange и веб-службы Exchange (EWS)</p></td>
<td><p>Хранение контактов; данные календаря</p></td>
</tr>
<tr class="even">
<td><p>Единая система обмена сообщениями Exchange и веб-службы Exchange</p></td>
<td><p>Журналы вызовов, список голосовой почты, голосовая почта</p></td>
</tr>
<tr class="odd">
<td><p>Параметры DHCP 120</p></td>
<td><p>Если запись DNS SRV недоступна, то для обнаружения регистратора клиент будет пытаться использовать параметр DHCP 120. Чтобы это работало, необходимо либо настроить сервер DHCP, либо включить поддержку DNSP в сервере Lync Server 2013. Подробные сведения см. в разделе &quot;Требования к оборудованию и программному обеспечению для устойчивости сайтов филиалов&quot; статьи <a href="lync-server-2013-branch-site-resiliency-requirements.md">Требования к устойчивости для сайтов филиала для Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>


## Функции обеспечения голосовой связи

Если предыдущие требования и рекомендации реализованы, то резервным пулом регистратора будут предоставляться следующие функции голосовой связи.

  - Исходящие вызовы ТСОП.

  - Входящие вызовы ТСОП, если поставщик услуг телефонной связи поддерживает возможность отработки отказа на резервный сайт.

  - Корпоративные вызовы между пользователями как одного сайта, так и разных сайтов.

  - Базовая обработка вызова, включая удержание, возобновление и переключение вызовов.

  - Двусторонний обмен мгновенными сообщениями и совместное использование аудио и видео пользователями на одном сайте.

  - Услуги переадресации вызовов, одновременных звонков в нескольких конечных точках, делегирования вызовов и групповых звонков, но только если обе стороны делегирования вызова или все члены группы настроены на одном и том же сайте.

  - Продолжение функционирования существующих телефонов и клиентов.

  - Регистрация вызовов (CDR).

  - Проверка подлинности и авторизация.

Когда основной центральный сайт выходит из строя, могут также работать следующие функции голосовой связи (в зависимости от того, как они были настроены).

  - Размещение и извлечение голосовых сообщений.
    
    Если необходимо, чтобы при выходе из строя основного центрального сайта оставалась доступной единая система обмена сообщениями Exchange, то необходимо выполнить одно из следующих действий.
    
      - Изменить запись DNS SRV таким образом, чтобы серверы единой системы обмена сообщениями Exchange на центральном сайте указывали на резервные серверы единой системы обмена сообщениями Exchange на другом сайте.
    
      - Настроить абонентскую группу единой системы обмена сообщениями Exchange таким образом, чтобы она включала серверы единой системы обмена сообщениями Exchange как на центральном, так и на резервном сайте, но определяла резервные серверы единой системы обмена сообщениями Exchange как отключенные. Если центральный сайт становится недоступным, то администратор Exchange должен пометить серверы единой системы обмена сообщениями Exchange на резервном сайте как включенные.
    
    Если ни одно из этих решений невозможно, то единая система обмена сообщениями Exchange не будет доступна в случае, если центральный сайт выйдет из строя.

  - Конференц-связь всех типов.
    
    Пользователь, который в результате отработки отказа оказался на резервном сайте, может присоединяться к конференции, созданной или размещенной тем организатором, чей пул доступен, но не может создавать или размещать конференцию в своем основном пуле, который стал недоступен. Аналогично, другие пользователи не могут присоединяться к конференциям, размещенным в основном пуле пользователя, вовлеченного в отработку отказа.

Следующие функции голосовой связи не будут работать в случае выхода из строя основного центрального сайта.

  - Автосекретарь конференции.

  - Функция присутствия и маршрутизация на основе DND.

  - Обновление параметров переадресации вызовов.

  - Служба "Группа ответа" и парковка вызовов.

  - Подготовка новых телефонов и клиентов.

  - Веб-поиск в адресной книге

## См. также

#### Другие ресурсы

[Планирование устойчивости голосовой связи для сайта филиала в Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md)


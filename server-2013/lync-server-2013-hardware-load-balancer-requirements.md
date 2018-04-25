﻿---
title: 'Lync Server 2013: требования к подсистеме балансировки нагрузки оборудования'
TOCTitle: Требования к подсистеме балансировки нагрузки оборудования
ms:assetid: 32891268-2059-43d0-adf4-af4ff1e9ce66
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ656815(v=OCS.15)
ms:contentKeyID: 49887938
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Требования к подсистеме балансировки нагрузки оборудования для Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Топология масштабированной и консолидированной среды пограничных серверов Lync Server 2013 оптимизирована для балансировки нагрузки через DNS в новых развертываниях, образующих федерацию с другими организациями с помощью Lync Server. Если для какого-либо из перечисленных ниже сценариев требуется высокая степень доступности, в пулах пограничных серверов сервер необходимо использовать аппаратный балансировщик нагрузки.

  - Образование федерации с организациями с помощью Office Communications Server 2007 R2 или Office Communications Server 2007

  - Система обмена сообщениями Exchange для удаленных пользователей, применяющих версию обмена сообщениями Exchange, предшествующую Exchange 2010 с пакетом обновления 1

  - Связь с пользователями общедоступных систем обмена сообщениями

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Использование в одном интерфейсе балансировки нагрузки через DNS, а в другом аппаратной балансировки нагрузки не поддерживается. Необходимо использовать либо ту, либо другую систему балансировки нагрузки для обоих интерфейсов.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При использовании аппаратной балансировки нагрузки балансировщик, развертываемый для соединений с внутренней сетью, необходимо настроить на балансировку нагрузки только трафика, идущего к серверам, на которых выполняются пограничная служба доступа и пограничная служба аудио- и видеоданных. Он не может балансировать нагрузку трафика, идущего ко внутренней пограничной службе веб-конференций или внутренней прокси-службе XMPP.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 не поддерживает преобразование сетевых адресов в режиме прямого ответа сервера (direct server return).</td>
</tr>
</tbody>
</table>


Чтобы определить, поддерживает ли ваш аппаратный балансировщик нагрузки функции, необходимые для Lync Server 2013, см. раздел о партнерах по балансировщику нагрузки на странице Lync Server 2010 по адресу [http://go.microsoft.com/fwlink/p/?linkId=202452](http://go.microsoft.com/fwlink/p/?linkid=202452).

## Требования к аппаратному балансировщику нагрузки для пограничных серверов, использующих пограничную службу аудио- и видеоданных

Аппаратный балансировщик нагрузки должен удовлетворять следующим требованиям, если используются пограничные серверы:

  - Отключите Nagle-оптимизацию TCP для внутреннего и внешнего портов 443. Оптимизация по алгоритму Nagle – это процесс объединения мелких пакетов сервера в один пакет большего размера для более эффективной передачи.

  - Отключите Nagle-оптимизацию TCP для диапазона внешних портов 50 000 - 59 999.

  - Не применяйте преобразование сетевых адресов на внутреннем или внешнем брандмауэре.

  - Пограничный внутренний интерфейс и внешний интерфейс пограничного сервера сервер должны находиться в разных сетях, и маршрутизацию между ними следует отключить.

  - Внешний интерфейс пограничного сервера сервер, на котором выполняется пограничная служба аудио- и видеоданных, должен использовать IP-адреса с открытой маршрутизацией, но никакого преобразования сетевых адресов или портов на всех внешних IP-адресах пограничного интерфейса.

## Требования к подсистеме балансировки нагрузки оборудования

Требования к использованию сходства на основе файлов cookie заметно сократились в Lync Server 2013 для веб-служб. Если при развертывании Lync Server 2013 вы не оставляете пограничные серверы переднего плана или пулы переднего планаLync Server 2010, вам не требуется сохраняемость на основе файлов cookie. Но если вы оставляете какие-либо пограничные серверы переднего плана или пулы переднего планаLync Server 2010 на временной или постоянной основе, вам следует по-прежнему использовать сохраняемость на основе файлов cookie, развернутую и настроенную для Lync Server 2010.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Если вы все же решите использовать сходство на основе файлов cookie, хотя вашему развертыванию оно и не требуется</strong>, это не будет иметь никаких отрицательных последствий.</td>
</tr>
</tbody>
</table>


Для развертываний, в которых **не будет использоваться** сходство на основе файлов cookie:

  - В правиле публикации обратного прокси-сервера через порт 4443, установите значение True для параметра **Перенаправлять заголовок узла** . Это обеспечит перенаправление исходного URL-адреса.

Для развертываний, в которых **будет использоваться** сходство на основе файлов cookie:

  - В правиле публикации обратного прокси-сервера через порт 4443, установите значение True для параметра **Перенаправлять заголовок узла** . Это обеспечит перенаправление исходного URL-адреса.

  - Файл cookie для аппаратного балансировщика нагрузки НЕ ДОЛЖЕН помечаться как httpOnly

  - Файл cookie для аппаратного балансировщика нагрузки НЕ ДОЛЖЕН быть ограничен сроком действия

  - Файл cookie для аппаратного балансировщика нагрузки ДОЛЖЕН иметь имя **MS-WSMAN** (веб-службы ожидают это значение, его нельзя менять)

  - Режим использования файлов cookie ДОЛЖЕН задаваться в каждом ответе HTTP, для которого входящий запрос HTTP не имел файла cookie, даже если файл cookie был уже получен предыдущим ответом HTTP в том же соединении TCP. Если балансировщик нагрузки при оптимизации допускает только одну вставку файла cookie для каждого соединения TCP, такая оптимизация НЕ ДОЛЖНА применяться

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В типичных конфигурациях аппаратного балансировщика нагрузки используется сходство исходных адресов и срок действия сеанса TCP 20 минут, что удобно для клиентов Lync Server и Lync 2013, поскольку состояние клиента поддерживается в течение времени работы клиентов или взаимодействия приложений.</td>
</tr>
</tbody>
</table>


При развертывании мобильных устройств ваш аппаратный балансировщик нагрузки должен поддерживать возможность балансировки нагрузки для индивидуальных запросов в рамках сеанса TCP (фактически необходима возможность балансировки нагрузки индивидуальных запросов на основе целевого IP-адреса).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В аппаратных балансировщиках нагрузки F5 имеется функция OneConnect, которая обеспечивает индивидуальную балансировку нагрузки для каждого запроса в соединении TCP. Если вы развертываете мобильные устройства, убедитесь, что поставщик вашего аппаратного балансировщика нагрузки поддерживает аналогичную функциональную возможность. Последним приложениям Apple iOS для мобильных устройств требуется протокол TLS версии 1.2. F5 предоставляет для этого специальные настройки.<br />
Подробные сведения о сторонних поставщиках аппаратных балансировщиков нагрузки см. в статье <a href="http://go.microsoft.com/fwlink/p/?linkid=230700">http://go.microsoft.com/fwlink/p/?linkId=230700</a></td>
</tr>
</tbody>
</table>


Ниже приводятся требования к аппаратному балансировщику нагрузки для веб-служб директора и интерфейсного пула.

  - Для внутренних виртуальных IP-адресов веб-служб задайте сохраняемость Source\_addr (внутренний порт 80, 443) на аппаратном балансировщике нагрузки. Для Lync Server 2013 сохраняемость Source\_addr означает, что множество соединений, исходящих с одного IP-адреса, всегда отправляются на один сервер для поддержания состояния сеанса.

  - В качестве таймаута простоя TCP используйте значение 1800 секунд.

  - На брандмауэре между обратным прокси-сервером и аппаратным балансировщиком нагрузки пула на следующем прыжке создайте правило, разрешающее HTTPS-трафик через порт 4443 из обратного прокси-сервера в аппаратный балансировщик нагрузки. В аппаратном балансировщике нагрузки необходимо настроить прослушивание портов 80, 443 и 4443.

## Сводка требований к сходству для аппаратного балансировщика нагрузки


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Расположение клиента или пользователя</th>
<th>Требования к сходству внешних доменных имен веб-служб</th>
<th>Требования к сходству внутренних доменных имен веб-служб</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>веб-приложение Lync Web App (внутренние и внешние пользователи)</p>
<p>Мобильное устройство (внутренние и внешние пользователи)</p></td>
<td><p>Без сходства</p></td>
<td><p>Сходство исходных адресов</p></td>
</tr>
<tr class="even">
<td><p>веб-приложение Lync Web App (только внешние пользователи)</p>
<p>Мобильное устройство (внутренние и внешние пользователи)</p></td>
<td><p>Без сходства</p></td>
<td><p>Сходство исходных адресов</p></td>
</tr>
<tr class="odd">
<td><p>веб-приложение Lync Web App (только внутренние пользователи)</p>
<p>Мобильное устройство (без развертывания)</p></td>
<td><p>Без сходства</p></td>
<td><p>Сходство исходных адресов</p></td>
</tr>
</tbody>
</table>


## Мониторинг порта для аппаратных балансировщиков нагрузки

Мониторинг порта на аппаратных балансировщиках нагрузки позволяет определить, когда конкретные службы становятся недоступными из-за ошибки оборудования или связи. Например, если служба сервера переднего плана (RTCSRV) останавливается из-за ошибки сервера переднего плана или пула переднего плана, функция мониторинга аппаратного балансировщика нагрузки прекращает получение трафика веб-службы служб. Благодаря использованию функции мониторинга порта в аппаратном балансировщике нагрузки можно отслеживать следующее:

### Пул пользователя сервера переднего плана – внутренний интерфейс аппаратного балансировщика нагрузки

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
<th>Виртуальный IP-адрес/порт</th>
<th>Порт узла</th>
<th>Компьютер/монитор узла</th>
<th>Профиль сохраняемости</th>
<th>Примечания.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;pool&gt;web-int_mco_443_vs</p>
<p>443</p></td>
<td><p>443</p></td>
<td><p>Сервер переднего плана</p>
<p>5061</p></td>
<td><p>Source (Источник)</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;pool&gt;web-int_mco_80_vs</p>
<p>80</p></td>
<td><p>80</p></td>
<td><p>Сервер переднего плана</p>
<p>5061</p></td>
<td><p>Source (Источник)</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>


### Пул пользователя сервера переднего плана – внешний интерфейс аппаратного балансировщика нагрузки

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
<th>Виртуальный IP-адрес/порт</th>
<th>Порт узла</th>
<th>Компьютер/монитор узла</th>
<th>Профиль сохраняемости</th>
<th>Примечания.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;pool&gt;web_mco_443_vs</p>
<p>443</p></td>
<td><p>4443</p></td>
<td><p>Сервер переднего плана</p>
<p>5061</p></td>
<td><p>Нет</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;pool&gt;web_mco_80_vs</p>
<p>80</p></td>
<td><p>8080</p></td>
<td><p>Сервер переднего плана</p>
<p>5061</p></td>
<td><p>Нет</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>

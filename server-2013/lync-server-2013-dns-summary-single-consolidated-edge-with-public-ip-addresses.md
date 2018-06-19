﻿---
title: 'Lync Server 2013: сводка по DNS — единая консолидированная пограничная топология с общедоступными IP-адресами'
TOCTitle: Сводка по DNS — единая консолидированная пограничная топология с общедоступными IP-адресами
ms:assetid: 7b83eae4-aa1a-4cc6-8077-42176d56cab5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205025(v=OCS.15)
ms:contentKeyID: 49310287
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по DNS — единая консолидированная пограничная топология с общедоступными IP-адресами в Lync Server 2013

 

_**Дата изменения раздела:** 2017-03-09_

Требования к записям DNS для удаленного доступа к Lync Server 2013 довольно просты, по сравнению с требованиями для сертификатов и портов. Кроме того, многие записи являются необязательными и зависят от настройки клиентов, на которых выполняется Lync 2013 и того, включена ли федерация.

Дополнительные сведения о требованиях Lync 2013 к DNS см. в статье [Определение требований DNS для Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Дополнительные сведения об автоматической настройке клиентов, на которых запущен Lync 2013, если не настроена разделенная DNS, см. в подразделе "Автоматическая настройка без разделенной DNS" раздела [Определение требований DNS для Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

В следующей таблице приведены сведения о DNS-записях, требуемых для поддержки единой консолидированной топологии сети периметра, показанной на рисунке "Единая консолидированная топология сети периметра". Обратите внимание, что некоторые DNS-записи требуются только для автоматической настройки клиентов Lync 2013 и Lync 2010. Если для настройки клиентов Lync вы планируете использовать объекты групповой политики, записи автоматической настройки не требуются.

## Важно. Требования сервер к сетевым адаптерам

Чтобы исключить проблемы маршрутизации, убедитесь, что в вашей роли пограничного сервера имеется хотя бы два сетевых адаптера, и что шлюз по умолчанию установлен только в сетевом адаптере, связанном с внешним интерфейсом. Например, как показано на рисунке "Топология единой и консолидированной среды пограничных серверов с общедоступными IP-адресами" в статье [Единая консолидированная пограничная топология с общедоступными IP-адресами в Lync Server 2013](lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md), шлюз по умолчанию будет указывать на внешний маршрутизатор в зоне Интернета или на брандмауэр, который может предоставить общедоступные IP-адреса. Отношение сетей для интерфейсов пограничного сервер – это отношение маршрутов вместо отношения преобразования сетевых адресов (NAT).

Для сетевых адаптеров на пограничном сервере вы можете использовать следующие настройки:

  - **Сетевой адаптер 1 (внутренний интерфейс)**
    
    Внутренний интерфейс с назначенным адресом 172.25.33.10.
    
    Шлюз по умолчанию не определен.
    
    Убедитесь в наличии маршрута между сетью, содержащей внутренний интерфейс пограничного сервера, и любыми сетями, содержащими серверы, на которых выполняются клиенты Lync Server 2013 или Lync Server 2013 (например, от 172.25.33.0 до 192.168.10.0).

  - **Сетевой адаптер 2 (внешний интерфейс)**
    
    Данному сетевому адаптеру назначаются три общедоступных IP-адреса, например 131.107.155.10 для пограничной службы доступа, 131.107.155.20 для пограничной службы веб-конференций и 131.107.155.30 для пограничной службы аудио- и видеосвязи.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для всех 3 интерфейсов пограничной службы можно использовать один IP-адрес, однако это не рекомендуется. Несмотря на экономию IP-адресов, в этом случае также потребуется 3 различных номера порта для каждой службы. По умолчанию используется TCP-порт 443, который гарантирует, что большинство удаленных брандмауэров будут разрешать трафик. Изменение номеров портов (например, TCP-порт 5061 для пограничного сервера доступа, TCP-порт 444 для пограничного сервера веб-конференций и TCP-порт 443 для пограничного сервера аудио- и видеоконференций) может привести к возникновению проблем у удаленных пользователей, если брандмауэр, за которым они расположены, не разрешает трафик через порты TCP-порты 5061 и 444. Кроме того, 3 отдельных IP-адреса упрощают устранение неполадок, поскольку позволяют выполнять фильтрацию по IP-адресу.</td>
    </tr>
    </tbody>
    </table>
    
    Общедоступный IP-адрес пограничной службы доступа является основным, с шлюзом по умолчанию, установленным в общедоступный маршрутизатор (131.107.155.1).
    
    Общедоступные IP-адреса пограничных служб веб-конференций и аудио- и видеосвязи являются дополнительными в разделе **Advanced (Дополнительно)** свойств **протокола IP версии 4 (TCP/IPv4)** и **протокола IP версии 6 (TCP/IPv6)** окна **Local Area Connection Properties (Свойства подключения по локальной сети)** в Windows Server.


> [!TIP]
> Настройка сервер с двумя сетевыми адаптерами – это один из двух возможных вариантов. Другой вариант – использование одного сетевого адаптера для внутренней части и трех сетевых адаптеров – для внешней части сервера сервер. Основное преимущество этого варианта – выделенный сетевой адаптер на службу сервер и сбор потенциально более кратких данных при необходимости поиска и устранения неполадок.



### Записи DNS, необходимые для единой и консолидированной среды пограничных серверов с общедоступными IP-адресами (пример)

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
<th>Полное доменное имя/DNS-запись</th>
<th>IP-адрес/полное доменное имя</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>131.107.155.10</p></td>
<td><p>Внешний интерфейс пограничного сервера доступа (Contoso). Требуется для всех доменов SIP с пользователями, для которых включена поддержка Lync.</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Внешний интерфейс пограничного сервера веб-конференций.</p></td>
</tr>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>Внешний интерфейс пограничного сервера аудио- и видеоконференций.</p></td>
</tr>
<tr class="even">
<td><p>Внешние DNS/SRV/443</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Внешний интерфейс пограничного сервера доступа. Требуется для автоматической настройки клиентов Lync 2013 и Lync 2010 для внешнего доступа. Требуется для всех доменов SIP с включенными пользователями Lync.</p></td>
</tr>
<tr class="odd">
<td><p>Внешние DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Внешний интерфейс пограничного сервера доступа SIP. Требуется для автоматического обнаружения DNS-записей федеративных партнеров, также называемых &quot;Разрешенные домены SIP&quot; (в предыдущих выпусках – расширенная федерация). Требуется для всех доменов SIP с включенными пользователями Lync.</p></td>
</tr>
<tr class="even">
<td><p>Внутренняя запись DNS/A</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Внутренний интерфейс консолидированного пограничного сервера</p></td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Записи, приведенные в предыдущей таблице, показаны с расширением <em>NET</em> или <em>COM</em> , чтобы подчеркнуть зону, в которой они должны размещаться, если не используется разделение DNS. Если используется разделение DNS, то все записи могут быть в одной зоне, и единственное отличие будет состоять в их внутренней или внешней версии. Подробные сведения см. в разделе &quot;Split-Brain DNS” (&quot;Разделение DNS&quot;) статьи <a href="lync-server-2013-determine-dns-requirements.md">Определение требований DNS для Lync Server 2013</a>.</td>
</tr>
</tbody>
</table>


## Записи, необходимые для федерации


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
<th>IP-адрес/запись полного доменного имени узла</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешние DNS/SRV/5061</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Внешний интерфейс пограничного сервера доступа SIP. Требуется для автоматического обнаружения DNS-записей федерации с другими возможными федеративными партнерами, также называемыми &quot;Разрешенные домены SIP&quot; (в предыдущих выпусках – расширенная федерация). Требуется для всех доменов SIP с пользователями, для которых включена поддержка Lync.</p>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Эта запись SRV необходима для функции &quot;Мобильность&quot; и расчетной палаты push-уведомлений</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
</tbody>
</table>


## Сводка по DNS – связь с Public Instant Messaging


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
<th>Полное доменное имя/DNS-запись</th>
<th>IP-адрес/полное доменное имя</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешний DNS/A</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>доступа интерфейс</p></td>
<td><p>Внешний интерфейс пограничного сервера доступа (Contoso). Требуется для всех доменов SIP с пользователями, для которых включена поддержка Lync.</p></td>
</tr>
</tbody>
</table>


## Сводка DNS для протокола Extensible Messaging and Presence Protocol


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
<th>IP-адрес/запись полного доменного имени узла</th>
<th>Сопоставление/комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешние DNS/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>Внешний интерфейс прокси-сервера XMPP, размещенного в доступа или пул. Требуется для всех внутренних доменов SIP с пользователями с включенной поддержкой Lync, для которых разрешен доступ к контактам XMPP в политике внешнего доступа. Доступ может быть настроен посредством глобальной политики, политики сайта, в котором находится пользователь, или политики, применяемой к конкретному пользователю с включенной поддержкой Lync. Кроме того, в политике федеративных партнеров XMPP необходимо настроить разрешенный домен XMPP. Дополнительные сведения см. в разделе <strong>См. также</strong>.</p></td>
</tr>
<tr class="even">
<td><p>Внешний DNS/A</p></td>
<td><p>xmpp.contoso.com (например)</p></td>
<td><p>IP-адрес доступа на сервер или пул, где размещается прокси-сервер XMPP</p></td>
<td><p>Укажите на доступа или пул, где размещается служба прокси-сервера XMPP. Как правило, создаваемая запись SRV указывает на эту запись размещения (A или AAAA)</p></td>
</tr>
</tbody>
</table>

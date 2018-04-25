﻿---
title: 'Lync Server 2013: сводка по сертификатам — масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с закрытыми IP-адресами и трансляцией сетевых адресов'
TOCTitle: Сводка по сертификатам — масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с закрытыми IP-адресами и трансляцией сетевых адресов
ms:assetid: 41677dbd-3d07-498a-8591-df255b606647
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425921(v=OCS.15)
ms:contentKeyID: 49309577
ms.date: 12/17/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Сводка по сертификатам — масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с закрытыми IP-адресами и трансляцией сетевых адресов в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-15_

Microsoft Lync Server 2013 использует сертификаты для взаимной проверки подлинности с другими серверами и для шифрования данных от сервера к серверу или от сервера к клиенту. Для сертификатов требуется соответствие имен записей DNS, связанных с серверами, с именем субъекта (SN) и альтернативным именем субъекта (SAN) в сертификате. Для успешного сопоставления серверов, записей DNS и записей сертификатов необходимо тщательно планировать предполагаемые полные доменные имена серверов, зарегистрированные в DNS и в записях SN и SAN сертификата.

Сертификат, назначенный внешним интерфейсам пограничного сервер зарегистрирован из общедоступного центра сертификации (ЦС). Общедоступные ЦС, успешно поставляющие сертификаты в целях коммуникации, перечислены в следующей статье: [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=929395](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=929395) При запросе сертификата можно использовать запрос, созданный развертывания Lync Server, создать запрос вручную или с помощью процесса, предоставляемого общедоступным ЦС. При назначении сертификата сертификат назначается интерфейсу доступа, интерфейсу веб-конференций и службе проверки подлинности аудио- и видеосеанса. Службу проверки подлинности аудио- и видеосеанса не следует путать с аудио- и видеоконференций, которая не использует сертификат для шифрования аудио- и видеопотоков. Внутренний интерфейс сервер может использовать сертификат от внутреннего (для организации) ЦС или сертификат от общедоступного ЦС. Сертификат внутреннего интерфейса использует только имя субъекта SN, и ему не нужны записи альтернативных имен субъектов SAN.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В следующей таблице показана вторая запись SIP (sip.fabrikam.com) в списке альтернативных имен субъекта для справки. Для каждого домена SIP в организации необходимо добавить соответствующее полное доменное имя, приведенное в списке альтернативных имен субъекта сертификата.</td>
</tr>
</tbody>
</table>


## Масштабируемая консолидированная пограничная топология, балансировка нагрузки на DNS с закрытыми IP-адресами и трансляцией сетевых адресов


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
<th>Альтернативные имена субъектов/порядок</th>
<th>Комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Масштабированная и консолидированная среда пограничных серверов (внешний периметр)</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>Сертификат должен быть от общедоступного ЦС, и должен иметь серверное EKU и клиентское EKU, если разворачивается общедоступная служба обмена мгновенными сообщениями с AOL. Кроме того, для масштабированного пограничного сервера закрытый ключ сертификата должен быть экспортируемым, и сертификат и его закрытый ключ должны быть скопированы в каждый пограничный сервер. Сертификат назначается внешним пограничным интерфейсам для следующих служб:</p>
<ul>
<li><p>Пограничная служба доступа</p></li>
<li><p>Пограничная служба конференций</p></li>
<li><p>Пограничная служба аудио- и видеоконференций</p></li>
</ul>
<p>Обратите внимание, что альтернативные имена субъектов добавляются в сертификат автоматически на основании ваших определений в построителе топологий. Вы по мере необходимости добавляете записи альтернативных имен субъектов для дополнительных доменов SIP и другие записи, поддержка которых необходима. Имя субъекта реплицируется в альтернативное имя субъекта и должно присутствовать для обеспечения правильной работы.</p></td>
</tr>
<tr class="even">
<td><p>Масштабированная и консолидированная среда пограничных серверов (внутренний периметр)</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>SAN не требуется</p></td>
<td><p>Сертификат может быть как от общедоступного, так и от внутреннего ЦС, и должен содержать серверное EKU. Сертификат назначается внутреннему пограничному интерфейсу.</p></td>
</tr>
</tbody>
</table>


## Сводка по сертификатам – возможность подключения к общедоступным службам обмена мгновенными сообщениями


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
<th>Имя субъекта</th>
<th>Альтернативные имена субъектов/порядок</th>
<th>Комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Внешняя пограничная служба/пограничная служба доступа</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>Сертификат должен быть выдан общим центром сертификации и должен содержать EKU для сервера и клиента EKU, если планируется развернуть возможность подключения к общедоступным службам обмена мгновенными сообщениями в AOL. Этот сертификат назначается внешним пограничным интерфейсам:</p>
<ul>
<li><p>Пограничная служба доступа</p></li>
<li><p>Пограничная служба конференций</p></li>
<li><p>Пограничная служба аудио- и видеоконференций</p></li>
</ul>
<p>Обратите внимание, что альтернативные имена субъектов добавляются в сертификат автоматически на основании ваших определений в построителе топологий. Вы по мере необходимости добавляете записи альтернативных имен субъектов для дополнительных доменов SIP и другие записи, поддержка которых необходима. Имя субъекта реплицируется в альтернативное имя субъекта и должно присутствовать для обеспечения правильной работы.</p></td>
</tr>
</tbody>
</table>


## Сводка по сертификатам протокола XMPP


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
<th>Имя субъекта</th>
<th>Альтернативные имена субъектов/порядок</th>
<th>Комментарии</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Назначить доступасервер или пул</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>xmpp.contoso.com</p>
<p><strong>*.contoso.com</strong></p></td>
<td><p>Первые три записи SAN – это обычные записи SAN для полной роли сервер. contoso.com – это запись, необходимая для федерации с XMPP-партнером на уровне корневого домена. Эта запись разрешает XMPP для всех доменов с суффиксом *.contoso.com.</p></td>
</tr>
</tbody>
</table>

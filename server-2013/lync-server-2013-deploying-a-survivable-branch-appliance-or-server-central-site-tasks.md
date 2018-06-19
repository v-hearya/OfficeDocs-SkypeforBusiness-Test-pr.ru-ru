﻿---
title: 'Lync Server 2013: развертывание устройства или сервера для обеспечения связи в филиалах — задачи центрального сайта'
TOCTitle: Развертывание устройства или сервера для обеспечения связи в филиалах — задачи центрального сайта
ms:assetid: 0f631a36-fc2e-41cd-8a0d-f27e84f4a89e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398189(v=OCS.15)
ms:contentKeyID: 49308955
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание устройства или сервера для обеспечения связи в филиалах с помощью Lync Server 2013 — задачи центрального сайта

 

_**Дата изменения раздела:** 2012-10-18_

Выполните задачи, описанные в данном разделе, на центральном сайте. Если вы развертываете сервер для обеспечения связи в филиалах, пропустите первую задачу.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед выполнением данных задач следует обеспечить выполнение следующих условий:
<ul>
<li><p>На центральном сайте следует настроить Lync Server.</p></li>
<li><p>Следует добавить техника по установке на сайте филиала в группу RTCUniversalSBATechnicians.</p></li>
</ul>
Кроме того, мы рекомендуем вам выполнить следующее:
<ul>
<li><p>Разверните DHCP-сервер на каждом сайте филиала, чтобы клиенты могли получать IP-адреса.</p></li>
<li><p>В качестве альтернативы развертыванию DHCP-сервера на каждом сайте филиала включите DHCP Lync Server на устройстве для обеспечения связи в филиалах или сервере для обеспечения связи в филиалах, используя командлет <strong>Set-CsRegistrarConfiguration –EnableDHCPServer $true</strong> командной строки Командная консоль Lync Server. Дополнительные сведения см. в подразделе «Требования к оборудованию и программному обеспечению» раздела <a href="lync-server-2013-branch-site-resiliency-requirements.md">Требования к устойчивости для сайтов филиала для Lync Server 2013</a> документации по планированию.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Содержание

  - [Добавление устройства для обеспечения связи в филиалах к Active Directory в Lync Server 2013](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md)

  - [Добавление сайтов филиалов в топологию в Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md)

  - [Определение устройства или сервера для обеспечения связи в филиалах в Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

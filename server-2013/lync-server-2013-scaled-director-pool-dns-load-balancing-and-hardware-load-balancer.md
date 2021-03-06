﻿---
title: 'Lync Server 2013: масштабируемый пул директоров — балансировка нагрузки на DNS и аппаратный балансировщик нагрузки'
TOCTitle: Масштабируемый пул директоров — балансировка нагрузки на DNS и аппаратный балансировщик нагрузки
ms:assetid: a1f6ffc0-9e6e-4217-a923-025c9679e154
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205142(v=OCS.15)
ms:contentKeyID: 49310710
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Масштабируемый пул директоров — балансировка нагрузки на DNS и аппаратный балансировщик нагрузки в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-22_

Масштабируемому Директоров, в котором для обеспечения дополнительной емкости и высокого уровня доступности развернуто несколько Директор, требуется балансировка нагрузки для распространения клиентских и серверных соединений между всеми членами пула. Директор содержит веб-службы, такие как переднего плана. Для балансировки нагрузки можно использовать аппаратную балансировку нагрузки либо балансировку нагрузки на DNS и аппаратную балансировку нагрузки. Поскольку балансировка нагрузки на DNS не удовлетворяет потребности веб-служб, в дополнении к ней используется аппаратная балансировка нагрузки.

В следующих разделах описывается планирование развертывания Директоров с использованием балансировки нагрузки на DNS и аппаратной балансировки нагрузки. Если вы планируете использовать только аппаратную балансировку для Директоров, см. раздел [Масштабируемый пул директоров — аппаратный балансировщик нагрузки в Lync Server 2013](lync-server-2013-scaled-director-pool-hardware-load-balancer.md), в котором описывается планирование этой топологии.

![Масштабируемый пул директоров](images/JJ205142.35a78a7a-b781-4c8f-951e-168451ba6a65(OCS.15).jpg "Масштабируемый пул директоров")

## Содержание

  - [Сводка по сертификатам — балансировка нагрузки на DNS и аппаратная балансировка нагрузки в Lync Server 2013](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Сводка по портам — балансировка нагрузки на DNS и аппаратная балансировка нагрузки в Lync Server 2013](lync-server-2013-port-summary-dns-and-hlb-load-balanced.md)

  - [Сводка по DNS — балансировка нагрузки на DNS и аппаратная балансировка нагрузки в Lync Server 2013](lync-server-2013-dns-summary-dns-and-hlb-load-balanced.md)


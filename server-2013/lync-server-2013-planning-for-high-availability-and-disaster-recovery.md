﻿---
title: 'Lync Server 2013: планирование высокой доступности и аварийного восстановления'
TOCTitle: Планирование высокой доступности и аварийного восстановления
ms:assetid: 15a72073-0336-45dd-b2a0-35e7522c6000
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204703(v=OCS.15)
ms:contentKeyID: 49309044
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Планирование высокой доступности и аварийного восстановления в Lync Server 2013

 

_**Дата изменения раздела:** 2013-10-31_

Как и в Lync Server 2010, основная схема обеспечения высокого уровня доступности для большинства ролей сервера Lync Server 2013 основывается на серверной избыточности благодаря использованию пулов. Если сервер с определенной ролью сервера выходит из строя, другие серверы в пуле, на которых работает та же роль, принимают на себя нагрузку этого сервера. Это относится к серверам переднего плана, пограничным серверам, серверам-посредникам и Директорам.

Сервер Lync Server 2013 добавляет новые меры аварийного восстановления интерфейсных пулов путем ввода географического распределения серверов в двух центрах обработки данных для обеспечения непрерывности обслуживания в случае выхода из строя одного пула или сайта.

Сервер Lync Server 2013 также обеспечивает высокий уровень доступности тылового сервера за счет поддержки синхронного зеркального отображения SQL для серверных баз данных.

В этом разделе рассматриваются основные компоненты обеспечения высокого уровня доступности и аварийного восстановления, а также действия по обеспечению высокого уровня доступности и аварийного восстановления для остальных серверных ролей.

## Содержание

  - [Аварийное восстановление пула переднего плана в Lync Server 2013](lync-server-2013-front-end-pool-disaster-recovery.md)

  - [Аварийное восстановление пограничного сервера в Lync Server 2013](lync-server-2013-edge-server-disaster-recovery.md)

  - [Планирование устойчивости корпоративной голосовой связи в Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md)

  - [Функции управления вызовами для аварийного восстановления в Lync Server 2013](lync-server-2013-call-management-features-for-disaster-recovery.md)

  - [Настройка сервера сохраняемого чата для обеспечения высокой доступности и аварийного восстановления в Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Устойчивость главного сайта Lync Server 2010](lync-server-2013-compatibility-with-lync-server-2010-metropolitan-site-resiliency.md)


﻿---
title: 'Lync Server 2013: поддержка хранения файлов'
TOCTitle: Поддержка хранения файлов
ms:assetid: ed66430d-3c19-4267-938c-956a51005073
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg399073(v=OCS.15)
ms:contentKeyID: 49311576
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Поддержка хранения файлов в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Сервер Lync Server 2013 использует одно хранилище для хранения всех файлов. Поддержка хранения файлов включает следующее.

  - Файловый ресурс общего доступа либо в непосредственно подключенной системе хранения (DAS – direct attached storage), либо в сети хранения данных (SAN), включая распределенную файловую систему (DFS) и массив RAID для хранения файлов. Дополнительные сведения о требованиях к системе хранения см. в разделе [Технические требования к серверам переднего плана, обмену мгновенными сообщениями и сведениями о присутствии в Lync Server 2013](lync-server-2013-technical-requirements-for-front-end-servers-instant-messaging-and-presence.md) и [Требования к оборудованию и программному обеспечению для директора в Lync Server 2013](lync-server-2013-hardware-and-software-requirements-for-the-director.md) документации по планированию. Подробные сведения о распределенной файловой системе (DFS) для Операционная система Windows Server 2008 см. в пошаговом руководстве по распределенным файловым системам в Windows Server 2008 по адресу [http://go.microsoft.com/fwlink/p/?linkId=202835](http://go.microsoft.com/fwlink/p/?linkid=202835).

  - Общий кластер для этого файлового ресурса общего доступа. Если используется общий кластер, то серверы кластера должны работать под управлением Windows Server 2008 или Windows Server 2008 R2. При использовании серверов кластера с более старыми версиями Windows могут возникнуть проблемы с разрешениями, которые приведут к недоступности некоторых компонентов. Создавать файловые ресурсы общего доступа можно с помощью администратора кластера. Подробные сведения об использовании администратора кластера см. в статье 284838 «Создание файлового ресурса кластера сервера с помощью программы Cluster.exe» базы знаний Майкрософт по адресу [http://go.microsoft.com/fwlink/p/?linkId=140899](http://go.microsoft.com/fwlink/p/?linkid=140899).

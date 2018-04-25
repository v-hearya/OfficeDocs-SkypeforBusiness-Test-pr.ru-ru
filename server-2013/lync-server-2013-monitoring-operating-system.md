﻿---
title: 'Lync Server 2013: мониторинг операционной системы'
TOCTitle: Мониторинг операционной системы
ms:assetid: 72406d3e-54c8-4796-8d6d-2144a5b6f030
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn720918(v=OCS.15)
ms:contentKeyID: 62246669
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Мониторинг операционной системы в Lync Server 2013

 

_**Дата изменения раздела:** 2015-01-26_

Мониторинг необходимо выполнять для всех серверов и компонентов Lync Server 2013. Очевидно, что самыми важными компонентами является сама операционная система. Lync Server 2013 поддерживает следующие версии x64:

  - Windows Server 2008 R2

  - Windows Server 2012 и Windows Server 2012 R2

Самым прозрачным способом мониторинга операционной системы является использование пакета управления операционной системы Windows Server. В нем представлены основные базовые компоненты мониторинга, такие как производительность, работоспособность и доступность для компьютеров под управлением Windows Server 2012, Windows Server 2012 R2 и Windows Server 2008 R2.

С помощью обнаружения, оповещения и автоматического отклика на важные события и индикаторы производительности данные пакеты управления сокращают время разрешения неполадок и повышают общую доступность и производительность систем под управлением ОС Windows Server.

Помимо соответствующих пакетов управления Windows Server для System Center Operations Manager можно использовать следующие системные инструменты и ресурсы для отслеживания работоспособности операционной системы (зависит от версии ОС).

## Windows Server 2008 R2

Windows Server 2008 R2 содержит следующие дополнительные возможности и инструменты, которые помогают администраторам в рамках базового мониторинга и управления ОС:

  - **Мониторинг ресурсов Windows** является мощным инструментом для понимания того, как процессы и службы используют системные ресурсы. В дополнение к отслеживанию использования ресурсов в режиме реального времени мониторинг ресурсов помогает в анализе неотвечающих процессов, определении использующих файл приложений, а также контроле процессов и служб.

  - **Компонент анализа надежности** является встроенным агентом, который предоставляет подробную информацию о взаимодействии в рамках использования и надежности системы. Данная информация раскрывается посредством интерфейса WMI с целью предоставления доступности для процесса потребления с помощью систем портативного считывания. Воздействуя на компонент анализа надежности с помощью интерфейса WMI, разработчики могут выполнять мониторинг и анализ приложений при одновременном повышении уровня надежности и производительности.

  - **Windows Server 2008 R2** использует встроенный компонент анализа надежности для вычисления индекса надежности, который предоставляет информацию об использовании и надежности системы за период времени в целом. Компонент анализа надежности также отслеживает любые важные изменения системы, которые могут повлиять на стабильность, например обновления Windows и установки приложений.

## Windows Server 2008 - мониторинг надежности и производительности Windows

Мониторинг надежности и производительности Windows является оснасткой MMC, которая объединяет в себе возможности предыдущих автономных инструментов, включая журналы и оповещения о производительности, советника по производительности сервера и мониторинг системы. Также предоставляет графический интерфейс для настройки сбора данных производительности и сеансов трассировки событий.

Функциональность также включает в себя мониторинг надежности, оснастку MMC, которая отслеживает изменения в системе и сравнивает их в рамках системной надежности, и предоставляет графический вид данных связей.

## Мониторинг надежности и производительности Windows

Помимо объединения мониторингом надежности и производительности Windows возможностей некоторых предыдущих автономных инструментов, таких как журналы и оповещения о производительности, мониторинг системы и советник по производительности сервера, предоставляется также некоторые новые возможности для Windows Server 2008 и Windows Server 2008 R2:

  - Наборы сборщика данных

  - Обзор ресурсов

  - Мониторинг надежности

  - Мастера и шаблоны для создания журналов

**Набор сборщика данных** группирует сборщиков данных в повторно используемые элементы для применения в разных сценариях мониторинга производительности. После сохранения группы сборщиков данных как набора сборщика данных операции, такие как планирование, могут быть применены ко всему набору через изменение одного свойства. Мониторинг надежности и производительности Windows содержит стандартные шаблоны набора сборщика данных для помощи системным администраторам в незамедлительном начале сбора данных производительности, которые характерны для серверной роли или сценария мониторинга.

Главная страница мониторинга надежности и производительности Windows является новым экраном **обзора ресурсов**, на котором представлен графический обзор ЦП в режиме реального времени, дисков, сети и использования памяти. Разворачивая каждый из этих отслеживаемых элементов, системные администраторы могут определить процессы, которые используют определенные ресурсы. В более ранних версиях Windows эти характерные для процесса текущие данные были доступны только в ограниченной форме в диспетчере задач.

**Мониторинг надежности** вычисляет индекс стабильности системы, который отражает, понизили ли непредвиденные проблемы уровень надежности системы. График индекса стабильности со временем быстро определяет данные при возникновении проблем. Сопутствующий отчет о стабильности системы предоставляет сведения для устранения причин понижения уровня надежности. С помощью просмотра изменений в системе (установка или удаление приложений, обновлений ОС, добавления или изменения драйверов) совместно со сбоями в работе (ошибки приложений, сбои ОС или аппаратные сбои) можно быстро разработать стратегию по решению данных неполадок.

Добавление счетчиков в файлы журнала и планирование их запуска, остановки или длительности теперь можно выполнять с помощью **интерфейса мастера**. Кроме того, сохранение данной конфигурации как шаблона позволяет системным администраторам собирать один и тот же журнал на других компьютерах без повторения выбора сборщика данных и процессов планирования. Возможности журналов производительности и оповещений были встроены в мониторинг надежности и производительности Windows для использования с любым сборщиком данных.

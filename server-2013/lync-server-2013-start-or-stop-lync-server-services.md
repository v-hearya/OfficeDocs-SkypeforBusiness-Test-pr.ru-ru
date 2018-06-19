﻿---
title: Запуск или остановка служб Lync Server 2013
TOCTitle: Запуск или остановка служб Lync Server 2013
ms:assetid: 1c70b4ec-9de5-4f7a-a3c9-c0eb76710505
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520958(v=OCS.15)
ms:contentKeyID: 49309116
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Запуск или остановка служб Lync Server 2013

 

_**Дата изменения раздела:** 2014-02-05_

Вы можете использовать панель управления Lync Server, чтобы запустить или остановить все службы системы Lync Server 2013, выполняемые на отдельном компьютере, либо запустить или остановить конкретную службу.

## Запуск или остановка всех служб Lync Server на компьютере

1.  Войдите на любой компьютер, подключенный к сети, где развернут Lync Server 2013, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsServerAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Topology** (Топология), а затем **Status** (Состояние).

4.  На странице **Status** (Состояние) отсортируйте список или выполните по нему поиск, чтобы найти компьютер с требуемыми службами, а затем щелкните его.

5.  Щелкните элемент **Action** (Действие).

6.  Щелкните **Start All services** (Запустить все службы) или **Stop All services** (Остановить все службы).

## Запуск или остановка конкретной службы

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Topology** (Топология), а затем **Status** (Состояние).

4.  На странице **Status** (Состояние) отсортируйте список или выполните по нему поиск, чтобы найти компьютер с требуемыми службами, а затем щелкните его.

5.  Щелкните элемент **Properties** (Свойства).

6.  Отсортируйте список служб, если это необходимо, и щелкните службу, которую хотите запустить или остановить.

7.  Щелкните элемент **Action** (Действие).

8.  Щелкните **Start service** (Запустить службу) или **Stop service** (Остановить службу).

9.  Нажмите кнопку **Close** (Закрыть).

## См. также

#### Задачи

[Запрет сеансов для служб в Lync Server 2013](lync-server-2013-prevent-sessions-for-services.md)  

#### Другие ресурсы

[Управление топологией Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

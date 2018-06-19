﻿---
title: 'Lync Server 2013: определение IP-адреса для шлюза SIP/CSTA'
TOCTitle: Определение IP-адреса для шлюза SIP/CSTA
ms:assetid: ae944057-3ad6-4474-a09b-81a3d27bd50f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg602125(v=OCS.15)
ms:contentKeyID: 49310862
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Определение IP-адреса для шлюза SIP/CSTA в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-21_

Если планируется подключение Lync Server к шлюзу SIP/CSTA, развернутому для удаленного управления звонками, с помощью протокола TCP, вам потребуется задать IP-адрес шлюза в топологий. Для шлюзов, поддерживающих соединения TLS, этот шаг является необязательным. Вы можете пропустить его и продолжить развертывание удаленного управления звонками (см. раздел [Включение удаленного управления звонками для пользователей Lync в Lync Server 2013](lync-server-2013-enable-lync-users-for-remote-call-control.md)).

## Задание IP-адреса шлюза SIP/CSTA с помощью построителя топологий

1.  Войдите на компьютер, где установлен построитель топологий, с использованием учетной записи, входящей в группу администраторов домена и группу RTCUniversalServerAdmins.

2.  Запустите построитель топологий: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Построитель топологий Lync Server**.

3.  Выберите загрузку существующей топологии.

4.  Разверните узел **Trusted application servers** (Доверенные серверы приложений).

5.  Щелкните правой кнопкой мыши созданный пул доверенных приложений (инструкции по созданию пула см. в разделе [Настройка записи доверенного приложения для удаленного управления звонками в Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)) и выберите команду **Изменить свойства** .

6.  Снимите флажок **Enable replication of configuration data to this pool** (Включить репликацию данных конфигурации для этого пула).

7.  Щелкните **Limit service usage to selected IP addresses** (Разрешить использовать службу только указанным IP-адресам). По умолчанию используется параметр **Use all configured IP addresses** (Использовать все настроенные IP-адреса).

8.  В текстовом поле **Primary IP address** (Основной IP-адрес) введите IP-адрес шлюза SIP/CSTA.

9.  Чтобы обновить топологию в центральном хранилище управления, в дереве консоли выберите узел **Lync Server** и затем на панели **Действия** щелкните **Опубликовать** .

## См. также

#### Задачи

[Настройка статического маршрута для дистанционного управления вызовами в Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md)  
[Настройка записи доверенного приложения для удаленного управления звонками в Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)

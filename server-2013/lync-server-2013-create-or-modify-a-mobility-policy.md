﻿---
title: Создание или изменения политики мобильности
TOCTitle: Создание или изменения политики мобильности
ms:assetid: fc2dfea0-2215-440d-9f4b-7c985da29211
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ721946(v=OCS.15)
ms:contentKeyID: 49888275
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание или изменения политики мобильности

 

_**Дата изменения раздела:** 2013-02-23_

Вы можете создать или изменить политику мобильности, чтобы позволить мобильным пользователям использовать поддерживаемые мобильные устройства для доступа к функциональным возможностям Lync, таким как обмен мгновенными сообщениями, сведения о присутствии и контакты. Вы можете создавать или изменять политики мобильности в панели управления Lync Server 2013 или в командная консоль Lync Server 2013

## Создание политики мобильности из панели управления Lync Server

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Клиенты** и затем нажмите кнопку навигации **Политика мобильности**.

4.  На странице **Политика мобильности** нажмите кнопку **Создать** и выполните одно из следующих действий:
    
    1.  Чтобы создать политику мобильности сайта, щелкните элемент **Политика сайта**, выберите сайт, нажмите кнопку **ОК**, просмотрите параметры по умолчанию и при необходимости измените их.
    
    2.  Чтобы создать политику мобильности сайта, щелкните элемент **Политика пользователя**, выберите имя, просмотрите параметры по умолчанию и при необходимости измените их.

5.  Нажмите кнопку **Сохранить**.

## Изменение политики мобильности из панели управления Lync Server

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **Клиенты** и затем нажмите кнопку навигации **Политика мобильности**.

4.  На странице **Политика мобильности** выберите одну из существующих политик мобильности.

5.  В меню **Правка** выберите пункт **Подробнее**.

6.  Измените параметры.

7.  Нажмите кнопку **Сохранить**.

## Удаление политик внешнего доступа с помощью командлетов Windows PowerShell

Политики мобильности также можно создавать (на уровне сайтов или индивидуальных пользователей) с помощью Windows PowerShell и командлета **New-CsMobilityPolicy**. Кроме того, вы можете использовать командлет **Set-CsMobilityPolicy** для изменения любых существующих политик, включая глобальную. Эти командлеты можно выполнять из командная консоль Lync Server 2013 или из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Создание политики мобильности на уровне сайта

  - Данная команда создает новую политику мобильности для сайта Redmond:
    
        New-CsMobilityPolicy -Identity "site:Redmond"
    
    Для всех свойств таких политик будут использоваться значения по умолчанию, так как в приведенной выше команде не заданы никакие параметры, кроме обязательного параметра Identity.

## Создание политики мобильности на уровне индивидуального пользователя

  - Чтобы создать политику мобильности на уровне пользователя, укажите для нее уникальный параметр Identity:
    
        New-CsMobilityPolicy -Identity "RedmondMobilityPolicy"

## Изменение значения отдельного свойства при создании политики мобильности

  - Чтобы создать политики, использующие разные значения свойства, включайте в них соответствующий параметр со значением. Например, следующая команда создает политику мобильности, отключающую возможность "Позвонить с рабочего":
    
        New-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False

## Изменение значений нескольких свойств при создании политики мобильности

  - Посредством включения нескольких параметров можно изменять значения нескольких свойств. Например, следующая команда создает политику, отключающую как мобильность, так и возможность "Позвонить с рабочего":
    
        New-CsMobilityPolicy "site:Redmond" -EnableMobility $False -EnableOutsideVoice $False

Дополнительные сведения см. в разделе справки для командлетов [New-CsMobilityPolicy](new-csmobilitypolicy.md) и [Set-CsMobilityPolicy](set-csmobilitypolicy.md).

## См. также

#### Задачи

[Настройка политики мобильных устройств в Lync Server 2013](lync-server-2013-configuring-mobility-policy.md)

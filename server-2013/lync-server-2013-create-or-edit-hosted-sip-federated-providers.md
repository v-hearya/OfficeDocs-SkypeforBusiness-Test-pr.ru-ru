﻿---
title: 'Lync Server 2013: создание или изменение размещенных федеративных поставщиков SIP'
TOCTitle: Создание или изменение размещенных федеративных поставщиков SIP
ms:assetid: 0dd6dcb6-a88d-46b8-9c96-b35967309bcd
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ552445(v=OCS.15)
ms:contentKeyID: 49308935
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание или изменение размещенных федеративных поставщиков SIP в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-19_

Средства коммуникации с помощью мгновенных сообщений, предоставляемые поставщиком услуг, размещенным в узле, позволяют пользователям организации использовать мгновенные сообщения для взаимодействия с пользователями служб мгновенных сообщений, предоставляемых размещенными в узлах поставщиками, включая Microsoft Office 365 и Lync Online.

Каждый размещенный в узле поставщик настраивается с полным доменным именем пограничного сервера поставщика услуг и уровнем проверки по умолчанию **Разрешить пользователям взаимодействовать только с людьми в своих списках контактов, которые пользуются услугами данного поставщика** .

Следующая процедура используется для создания и изменения размещенных в узлах поставщиков:

## Чтобы создать или изменить размещенных в узлах поставщиков

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Федерация и внешний доступ** , затем щелкните **Федеративные поставщики SIP** .

4.  Если требуется создать нового размещенного в узле поставщика, щелкните **Создать** , а затем щелкните **Размещенный в узле поставщик** .

5.  Если требуется изменить запись из списка размещенных в узлах поставщиков, выберите размещенного в узле поставщика, щелкните **Изменить** , затем щелкните **Показать подробности** .

6.  На странице **Изменить федеративного поставщика SIP** можно указать или изменить следующие параметры.
    
      - **Включить связь с данным поставщиком**    При выборе этого параметра разрешается связь с пользователями данного поставщика.
    
      - **Имя поставщика:**    обязательное свойство, введите имя поставщика, каким оно будет отображаться в списке федеративных поставщиков SIP.
    
      - **Служба пограничного доступа (полное доменное имя):**    Обязательное свойство, введите полное доменное имя службы пограничного доступа размещенного в узле поставщика, настройку которого выполняете. Эти сведения должны предоставляться размещенным в узле поставщиком и их допускается изменять только в том случае, если размещенный в узле поставщик изменяет полное доменное имя службы пограничного доступа на размещенном в узле поставщике.
    
      - **Уровень проверки по умолчанию:**    параметр по умолчанию **Разрешить пользователям взаимодействовать с людьми в своих списках контактов, которые используют этого поставщика** ограничивает связь с контактами, принятые данным пользователем и включенным им в свой список контактов.
        
        При выборе параметра **Разрешить связь со всеми, кто пользуется услугами данного поставщика** снимается ограничение, содержащее требование получения и принятия приглашения установить контакт. Этим параметром не ограничивается круг пользователей, которые могут связываться с вами из сети размещенного в узле поставщика.

7.  Завершив настройку параметров, нажмите кнопку **Сохранить** , чтобы сохранить параметры, или **Отмена** , чтобы отменить изменения.

## См. также

#### Задачи

[Конфигурация политик для управления общим доступом пользователей в Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)  
[Включение или отключение федерации и подключение для общедоступного обмена мгновенными сообщениями в Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

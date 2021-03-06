﻿---
title: Отключение и повторное включение учетных записей пользователей для Lync Server
TOCTitle: Отключение и повторное включение учетных записей пользователей для Lync Server
ms:assetid: 12497d00-f665-4a97-be68-854c5a8be4fc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg429696(v=OCS.15)
ms:contentKeyID: 49308999
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Отключение и повторное включение учетных записей пользователей для Lync Server

 

_**Дата изменения раздела:** 2016-04-04_

Для отключения ранее включенной учетной записи в Lync Server 2013 без потери параметров Lync Server, настроенных для этой учетной записи, можно использовать следующую процедуру. Так как параметры учетной записи Lync Server не теряются, можно снова включить ранее включенную учетную запись без необходимости в перенастройке этой учетной записи.

## Чтобы отключить или повторно включить ранее включенную учетную запись пользователя для Lync Server

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Пользователи**.

4.  В поле **Search users** введите отображаемое имя (полностью или первую его часть), имя, фамилию, имя учетной записи SAM (Security Accounts Manager — диспетчер учетных записей безопасности), SIP-адрес или линейный идентификатор URI (Uniform Resource Identifier — универсальный код ресурса) учетной записи пользователя, которую требуется отключить или активировать повторно, а затем щелкните **Найти**.

5.  В таблице щелкните учетную запись пользователя, которую необходимо отключить или активировать повторно.

6.  В меню **Действие** выполните одно из следующих действий:
    
      - Для временного отключения учетной записи пользователя для Lync Server 2013 щелкните **Временно отключить для Lync Server**.
    
      - Чтобы включить учетную запись пользователя для Lync Server 2013, щелкните **Повторно включить для Lync Server**.

## Отключение и повторное включение учетной записи пользователя с помощью командлетов Windows PowerShell

Учетные записи пользователей можно также временно отключать, а позднее снова включать, пользуясь командлетом **Set-CsUser**. Данный командлет может запускаться или из командная консоль Lync Server 2013, или из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Отключение учетной записи пользователя

  - Чтобы временно отключить учетную запись пользователя, установите значение свойства "Enabled" равным False ($False). Пример:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $False

## Повторное включение учетной записи пользователя

  - Чтобы повторно включить отключенную учетную запись пользователя, установите значение свойства "Enabled" равным True ($True). Пример:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $True

Дополнительные сведения см. в статье справки по командлету [Set-CsUser](set-csuser.md).

## См. также

#### Задачи

[Добавление и включение новой учетной записи пользователя для Lync Server](lync-server-2013-add-and-enable-user-account-for-lync-server.md)  

#### Другие ресурсы

[Подключение и отключение пользователей для Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)


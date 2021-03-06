﻿---
title: Развертывание пилотного пула Lync Server 2013
TOCTitle: Развертывание пилотного пула Lync Server 2013
ms:assetid: 19c27053-8b21-401f-ad91-75c2dd355e91
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204718(v=OCS.15)
ms:contentKeyID: 49309092
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание пилотного пула Lync Server 2013

 

_**Дата изменения раздела:** 2013-11-22_

Одним из первых этапов миграции в Lync Server 2013 является развертывание пилотного пула. Пилотный пул служит для тестирования сосуществования Lync Server 2013 с развертыванием Office Communications Server 2007 R2. Сосуществование — это временное состояние, которое длится до тех пор, пока все пользователи и пулы не будут перенесены в Lync Server 2013.

При развертывании пилотной версии пула используется мастер определения нового интерфейсного пула. Необходимо выполнить развертывание тех же компонентов и рабочих нагрузок в пилотной версии Lync Server 2013, установленной в пуле Office Communications Server 2007 R2. Если при развертывании сервера архивации, сервера мониторинга или System Center Operations Manager для архивации и мониторинга среды Office Communications Server 2007 R2 требуется продолжить архивацию или мониторинг на период миграции, необходимо также развернуть эти компоненты в пилотной версии среды. Версия, развертываемая для архивации и мониторинга среды Office Communications Server 2007 R2 не охватывает данные в среде Lync Server 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Ниже рассматриваются компоненты и параметры, которые следует включить в общий процесс развертывания пилотного пула. В этом разделе указаны только основные моменты, которые следует учесть при развертывании. Подробные инструкции см. в руководстве <a href="lync-server-2013-deploying-lync-server.md">Развертывание Lync Server 2013</a>.</td>
</tr>
</tbody>
</table>


**Развертывание пилотного пула Lync Server 2013**

1.  Войдите на компьютер, где установлен построитель топологий, с использованием учетной записи, входящей в группу администраторов домена и группу RTCUniversalServerAdmins.

2.  Откройте построитель топологий и выберите пункт "Создать новую топологию".

3.  Укажите основной домен SIP.
    
    ![Создание новой топологии, страница определения основного домена](images/JJ204718.68775d87-f32c-494a-8386-6d4c81e81284(OCS.15).jpg "Создание новой топологии, страница определения основного домена")

4.  Выполните все шаги мастера, пока не откроется мастер **Определение нового интерфейсного пула**. Нажмите кнопку "Далее".

5.  Введите полное доменное имя пула. При определении пилотного пула вы можете выбрать, следует ли развернуть переднего плана Enterprise Edition или Сервер Standard Edition. Lync Server 2013 не требует, чтобы компоненты пилотного пула совпадали с компонентами, развернутыми в старом пуле.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Полное доменное имя пула или сервера, задаваемое для пилотного пула, должно быть уникальным. Оно не должно совпадать с именем уже развернутого пула Office Communications Server 2007 R2 или других развернутых серверов.</td>
    </tr>
    </tbody>
    </table>
    
    ![Страница определения полного доменного имени пула переднего плана](images/JJ204718.5ff4336c-13fa-47cc-899b-066f267eb3f0(OCS.15).jpg "Страница определения полного доменного имени пула переднего плана")

6.  Определите компьютер, который будет добавлен в пул.
    
    ![Диалоговое окно определения нового пула переднего плана](images/JJ204718.374f0ed4-988b-465f-9861-8d1db401e76f(OCS.15).jpg "Диалоговое окно определения нового пула переднего плана")

7.  На странице **Выбор функций** установите флажки для функций, которые нужно развернуть в этом пуле переднего плана. Например, если вы развертываете только функции обмена сообщениями и сведениями о присутствии, установите флажок "Конференц-связь", чтобы разрешить многосторонние текстовые беседы, но не устанавливайте флажки "Конференц-связь с телефонным подключением (через ТСОП)", "Корпоративная голосовая связь" или "Контроль допуска звонков", так как они соответствуют функциям голосовой и видеосвязи, а также совместной работы. Дополнительные сведения о выборе функций см. в разделе [Определение и настройка пула переднего плана или сервера Standard Edition в Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md) документации по развертыванию.
    
    ![Пул переднего плана, страница выбора функции](images/JJ204718.5c3f3ff9-6e17-4d66-9b13-3bd55b38246b(OCS.15).jpg "Пул переднего плана, страница выбора функции")

8.  На странице **Выбор ролей серверов с совмещенным расположением** рекомендуется выровнять роль посредник в Lync Server 2013. При объединении устаревшей топологии с Lync Server 2013 необходимо сначала выровнять Office Communications Server 2007 R2посредник. После объединения топологий и настройки Lync Server 2013посредник можно сохранить совместно размещенную роль посредник или заменить ее на изолированный сервер при перемещении роли посредник на Lync Server 2013 позднее в процессе развертывания.
    
    ![Пул переднего плана, страница выбора ролей серверов с совмещенным расположением](images/JJ204718.e00b7eba-010b-44ed-b0a6-6ab3e534fb8c(OCS.15).jpg "Пул переднего плана, страница выбора ролей серверов с совмещенным расположением")

9.  При развертывании пилотного пула на странице **Связывание ролей сервера с этим пулом переднего плана** не выбирайте параметр **Включить пограничный пул для использования компонентом мультимедиа этого пула переднего плана**. Эту функцию нужно будет включить на более позднем этапе миграции. Пока оставьте этот флажок снятым.
    
    ![Страница связывания ролей серверов с пулами переднего плана](images/JJ204718.2d95a798-ad76-4dad-9392-ce41f4d938d1(OCS.15).jpg "Страница связывания ролей серверов с пулами переднего плана")

10. На странице **Выбор сервера Office Web Apps** нажмите кнопку **Создать** и укажите полное доменное имя сервера приложений.
    
    ![Определение нового сервера Office Online, свойства полного доменного имени](images/JJ204718.25c6b455-f1b8-4326-a569-6e338153d398(OCS.15).jpg "Определение нового сервера Office Online, свойства полного доменного имени")

11. На странице **Определение хранилища сервера архивации SQL Server** выберите экземпляр SQL Server, ранее созданный для Lync Server 2013.
    
    ![Страница определения хранилища архивации SQL Server](images/JJ204718.0f76f1dc-d0d7-42a0-aea3-400b8e1f35cd(OCS.15).jpg "Страница определения хранилища архивации SQL Server")

12. На странице **Определение хранилища сервера мониторинга SQL Server** выберите экземпляр SQL Server, ранее созданный для Lync Server 2013. Нажмите **Готово**.

13. На верхнем узле построителя топологий щелкните правой кнопкой мыши **Lync Server** и нажмите **Изменить свойства.** Выберите **Простые URL-адреса**.

14. Обновите **URL-адрес для административного доступа**.
    
    ![Изменение свойств, страница простых URL-адресов](images/JJ204718.ef596dd2-1983-47e0-b342-4fc7a0e36380(OCS.15).jpg "Изменение свойств, страница простых URL-адресов")
    
    Дополнительные сведения о простых URL-адресах см. в разделе [Изменить или настроить простые URL-адреса в Lync Server 2013](lync-server-2013-edit-or-configure-simple-urls.md) в документации по развертыванию.

15. В разделе **Изменить свойства** нажмите **Сервер централизованного управления**.

16. В раскрывающемся списке выберите пул Lync Server 2013.
    
    ![Изменение свойств, страница центрального сервера управления](images/JJ204718.211955fc-85f2-462d-8709-e6ea67092e89(OCS.15).jpg "Изменение свойств, страница центрального сервера управления")

17. Нажмите "ОК", чтобы закрыть страницу **Изменить свойства**.

18. В меню **Действие** выберите действие **Опубликовать топологию**.

19. По завершении процесса публикации нажмите кнопку **Готово** .

20. После возврата в мастер развертывания Lync Server 2013 выберите **Установить или обновить систему Lync Server**.
    
    ![Мастер развертывания Lync Server 2013](images/JJ204718.fb05adef-ad29-4905-9090-d409261b0e48(OCS.15).jpg "Мастер развертывания Lync Server 2013")

Инструкции по установке локальной копии хранилища конфигурации и запуску необходимых служб см. в разделе [Настройка серверов и пулов переднего плана для Lync Server 2013](lync-server-2013-setting-up-front-end-servers-and-front-end-pools.md) документации по развертыванию.



﻿---
title: Изменение голосового маршрута в Lync Server 2013
TOCTitle: Изменение голосового маршрута в Lync Server 2013
ms:assetid: afc562cc-8807-489b-8850-dbbe1c1ab9f5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412838(v=OCS.15)
ms:contentKeyID: 49310849
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Изменение голосового маршрута в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

В этом разделе даны инструкции по изменению маршрута голосовых вызовов. Инструкции по созданию маршрута см. в разделе [Создание голосового маршрута в Lync Server 2013](lync-server-2013-create-a-voice-route.md).

## Изменение маршрута голосовых вызовов

1.  Войдите на компьютер как член группы RTCUniversalServerAdmins или роли CsVoiceAdministrator, CsServerAdministrator или CsAdministrator. Дополнительные сведения см. в разделе [Делегирование разрешений на установку в Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации выберите пункт **Маршрутизация голосовой связи**, а затем — **Route**.

4.  На странице **Route** (Маршрут) измените маршрут голосовых вызовов с помощью одного из следующих методов:
    
      - Последовательно щелкните имя маршрута голосовых вызовов, **Edit** (Изменить) и **Show details** (Подробности).
    
      - Последовательно щелкните имя маршрута голосовых вызовов, **Edit** (Изменить), **Copy** (Копировать) и **Paste** (Вставить). Последовательно щелкните созданную копию маршрута голосовых вызовов, **Edit** (Изменить) и **Show details** (Подробности).

5.  На странице **Edit Voice Route** (Изменение маршрута голосовых вызовов) введите описательное имя маршрута голосовых вызовов в поле **Name** (Имя).

6.  В поле **Description** (Описание) введите дополнительные сведения о маршруте голосовых вызовов (необязательно).

7.  Чтобы указать шаблоны для маршрута, создайте регулярное выражение с помощью средства **Build a pattern to match** (Создание шаблона для поиска соответствия) или вручную.
    
      - Для создания регулярного выражения с помощью средства **Build a pattern to match** (Создание шаблона для поиска соответствия) введите значения, показанные ниже. Вы можете указать два типа поиска соответствия по шаблону:
        
          - **Starting digits for numbers that you want to allow** (Начальные цифры номеров): введите значения префикса, которые должен содержать этот маршрут (включая начальные цифры номера и остальные цифры при необходимости). Например, введите **+425** и затем щелкните **Add** (Добавить). Повторите этот шаг для каждого значения префикса, которое необходимо включить в маршрут.
        
          - **Исключения:** если требуется указать одно или несколько исключений для значения префикса, выделите префикс и затем щелкните **Исключения**. Введите одно или несколько значений для поиска соответствия по шаблону, которые *не* требуется включать в маршрут. Например, чтобы исключить из маршрута номера, начинающиеся с +425237, введите значение **+425237** в поле **Исключения** и затем нажмите кнопку **ОК**.
    
      - Чтобы задать шаблон поиска соответствия вручную, в средстве **Build a pattern to match** (Создание шаблона для поиска соответствия) щелкните **Edit** (Изменить) и затем введите регулярное выражение .NET Framework для указания шаблона поиска соответствия конечных номеров телефонов, к которым применяется маршрут. Дополнительные сведения о создании регулярных выражений см. в разделе "Регулярные выражения в .NET Framework" на веб-странице [http://go.microsoft.com/fwlink/?linkid=140927\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=140927%26clcid=0x419).

8.  Если вы не хотите, чтобы получатель звонка видел идентификатор телефона, используемого для исходящего вызова, выберите параметр **Скрыть идентификатор звонящего**. При выборе этого параметра вам также потребуется задать параметр **Дополнительный идентификатор звонящего**, который будет отображаться на экране получателя звонка.

9.  Чтобы связать один или несколько магистральных каналов ТСОП с маршрутом голосовых вызовов, нажмите кнопку **Добавить** и затем выберите магистральный канал в списке.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если развертывание содержит серверы-посредники Microsoft Office Communications Server 2007 R2, то они также будут доступны в списке.</td>
    </tr>
    </tbody>
    </table>


10. Чтобы связать один или несколько режимов работы с ТСОП с маршрутом голосовых вызовов, нажмите кнопку **Выбрать** и затем выберите запись в списке режимов работы с ТСОП, определенных для развертывания корпоративной голосовой связи.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Сведения о том, как просмотреть свойства каждой записи режима работы с ТСОП, см. в разделе <a href="lync-server-2013-view-pstn-usage-records.md">Просмотр записей использования ТСОП в Lync Server 2013</a>.<br />
    Сведения о создании или изменении записей режимов работы с ТСОП см. в разделе <a href="lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md">Создание голосовой политики и настройка записей использования ТСОП в Lync Server 2013</a> или <a href="lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md">Изменение голосовой политики и настройка записей использования ТСОП в Lync Server 2013</a>.</td>
    </tr>
    </tbody>
    </table>


11. Для обеспечения оптимальной производительности упорядочите записи режимов работы с ТСОП. Чтобы изменить расположение записи в списке, выделите запись и затем щелкните кнопку со стрелкой вверх или вниз.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для политики голосовой связи важен порядок, в котором перечислены режимы работы с ТСОП, а для маршрута голосовых вызовов — нет. Однако мы рекомендуем упорядочить список по частоте использования, например: RedmondLocal, RedmondLongDist, RedmondInternational, RedmondBackup. (Lync Server обходит список сверху вниз.)</td>
    </tr>
    </tbody>
    </table>


12. Введите значение в поле **Enter a translated number to test** (Введите преобразованный номер для проверки) и затем щелкните **Go** (Проверить) (необязательно). Результаты проверки отобразятся под полем.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если маршрут голосовых вызовов не прошел проверку, то вы можете сохранить его и проверить позже. Дополнительные сведения см. в разделе <a href="lync-server-2013-test-voice-routing.md">Тестирование голосовой маршрутизации в Lync Server 2013</a>.</td>
    </tr>
    </tbody>
    </table>


13. Нажмите кнопку **ОК**.

14. На странице **Route** (Маршрут) щелкните **Commit** (Фиксировать) и затем щелкните **Commit all** (Фиксировать все).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для публикации изменений конфигурации необходимо использовать команду <strong>Сохранить все</strong> при каждом изменении или создании маршрута голосовых вызовов. Дополнительные сведения см. в разделе <a href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Публикация ожидающих изменений в конфигурации маршрутизации голосовой связи в Lync Server 2013</a> документации по операциям.</td>
    </tr>
    </tbody>
    </table>


## См. также

#### Задачи

[Создание голосового маршрута в Lync Server 2013](lync-server-2013-create-a-voice-route.md)  
[Просмотр записей использования ТСОП в Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)  
[Создание голосовой политики и настройка записей использования ТСОП в Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Изменение голосовой политики и настройка записей использования ТСОП в Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  
[Публикация ожидающих изменений в конфигурации маршрутизации голосовой связи в Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  

#### Другие ресурсы

[Тестирование голосовой маршрутизации в Lync Server 2013](lync-server-2013-test-voice-routing.md)

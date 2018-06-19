﻿---
title: Создание или изменение параметров конфигурации собрания в Lync Server 2013
TOCTitle: Создание или изменение параметров конфигурации собрания в Lync Server 2013
ms:assetid: ce6773c1-a0d5-4405-8e32-33a6f3a46a1a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ721889(v=OCS.15)
ms:contentKeyID: 49888196
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание или изменение параметров конфигурации собрания в Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-23_

Можно использовать параметры на странице конфигурации собрания для определения различных характеристик процедуры присоединения к собранию. По умолчанию процедуру присоединения определяют глобальные параметры. Также можно создавать параметры присоединения к собранию на уровне сайта и на уровне пула. Если вы создаете параметры на уровне пула, эти параметры применяются ко всем собраниям, размещаемым этим пулом. Если вы не создаете параметры на уровне пула, применяются параметры, заданные на уровне сайта (при их наличии). Если вы не задали параметры на уровне сайта, ко всем собраниям применяются глобальные параметры.

## Создания параметров присоединения к новому собранию

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Конференц-связь**, а затем **Конфигурация собрания**.

4.  На странице **Конфигурация собрания** щелкните **Создать**, а затем выполните одно из следующих действий:
    
      - Чтобы создать политику на уровне сайта, щелкните **Конфигурация сайта**. В поле поиска **Выберите сайт** введите имя сайта (полностью или частично), для которого требуется определить параметры присоединения к собранию. В итоговом списке сайтов щелкните необходимый сайт, а затем щелкните **ОК**.
    
      - Чтобы создать политику на уровне пула, щелкните **Конфигурация пула**. В поле поиска **Выберите службу** введите имя службы пула (полностью или частично), для которой требуется определить параметры присоединения к собранию. В итоговом списке служб щелкните необходимый пул, а затем щелкните **ОК**.

5.  Чтобы направлять участников, набирающих номер из сети PSTN, в зал ожидания, снимите флажок **Обход зала ожидания абонентами PSTN**. По умолчанию участники, набирающие номер из сети PSTN, незамедлительно перенаправляются в собрание.

6.  Чтобы определить, кто может выступать на собрании, в области **Задать выступающего** выполните одно из следующих действий:
    
      - Чтобы выступать на собрании мог только его организатор, щелкните **Нет**.
    
      - Чтобы разрешить выступать на собрании только тем участникам, которые работают в организации, щелкните **Организация**. Это значение по умолчанию.
    
      - Чтобы разрешить выступать на собрании любому участнику, щелкните **Все**.

7.  Чтобы предоставить организатору возможность выбора типа конференции при планировании собрания, снимите флажок **Назначенный тип конференции по умолчанию**. По умолчанию тип конференции назначается автоматически.

8.  Чтобы предотвратить автоматический допуск анонимных (не прошедших проверку подлинности) пользователей на собрание, снимите флажок **Допускать анонимных пользователей по умолчанию**. По умолчанию анонимные пользователи автоматически допускаются на собрания.

9.  Чтобы настроить отправку участникам приглашения на собрание, выполните следующие действия. Обратите внимание, что максимальная длина URL-адресов и настраиваемых колонтитулов — 1 КБ. Если вы не укажете значение для настроек, они не будут включены в собрание (кроме **URL-адрес справки**). Если вы не включите настраиваемый URL-адрес справки, в приглашении будет отображаться URL-адрес справки по умолчанию для Lync.
    
      - Чтобы настроить логотип, который отображается в приглашении на собрание, укажите местоположение логотипа в поле **URL-адрес логотипа**.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>В качестве логотипа необходимо использовать изображение формата GIF или JPG, имеющее размер 188 на 30 пикселей.</td>
        </tr>
        </tbody>
        </table>
    
      - Чтобы настроить текст справки, который отображается в приглашении на собрание, введите расположение текста справки в поле **URL-адрес справки**.
    
      - Чтобы настроить юридическую информацию, которая отображается в приглашении на собрание, укажите местоположение в поле **URL-адрес правового документа**.
    
      - Чтобы настроить текст колонтитулов, которые отображаются в приглашении на собрание, введите текст в поле **Настраиваемый колонтитул**.

10. Щелкните **Commit** (Выполнить).

## Изменение существующей коллекции конфигураций собраний

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Conferencing** (Конференц-связь), а затем **Meeting Configuration** (Конфигурация собрания).

4.  В списке конфигураций собрания выберите конфигурацию, которую необходимо изменить, щелкните **Edit** (Правка), а затем выберите **Show details** (Показать подробности).

5.  В поле **Edit Meeting Configuration** (Изменить конфигурацию собрания) можно изменить любые параметры конфигурации, за исключением имени конфигурации, которое не подлежит изменению.

6.  Щелкните **Commit** (Выполнить).

## Создание параметров конфигурации нового собрания с помощью командлетов Windows PowerShell

Параметры конфигурации собрания можно создать (только на уровне сайта) с помощью оболочки Windows PowerShell и командлета New-CsMeetingConfiguration. Этот командлет можно запустить из командная консоль Lync Server 2013 или из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876)..

## Создание параметров конфигурации собрания, использующих значения по умолчанию

  - Эта команда создает новый набор параметров конфигурации собрания для сайта Redmond:
    
        New-CsMeetingConfiguration -Identity "site:Redmond"
    
    Так как при выполнении предыдущей команды не были указаны никакие параметры (кроме обязательного параметра Identity), для всех свойств новых параметров конфигурации собраний будут использоваться значения по умолчанию.

## Изменение значений свойств при создании параметров конфигурации собрания

  - Для создания настроек, использующих разные значения свойств, просто добавьте соответствующий параметр и значение параметра. Например, чтобы создать коллекцию параметров конфигурации собраний, которые по умолчанию допускают выступление всех участников на собрании, используйте следующую команду:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone"

## Изменение нескольких значений свойств при создании параметров конфигурации собрания

  - Многочисленные значения свойств можно изменить путем включения различных параметров. Например, эта команда допускает выступление любого участника на собрании, а также переводит пользователей PSTN в зал ожидания до их официального допуска к участию в собрании:
    
        New-CsMeetingConfiguration -Identity "site:Redmond" -DesignateAsPresenter "Everyone" -PSTNUCallersBypassLobby $True

Для получения дополнительной информации см. раздел справки по командлету [New-CsMeetingConfiguration](new-csmeetingconfiguration.md).

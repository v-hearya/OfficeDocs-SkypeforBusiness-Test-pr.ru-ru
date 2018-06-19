﻿---
title: Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013
TOCTitle: Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013
ms:assetid: 115a1a2c-599f-474c-a063-52f7144b5246
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520952(v=OCS.15)
ms:contentKeyID: 49308980
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013

 

_**Дата изменения раздела:** 2012-11-01_

Инструмент Intelligent IM Filter позволяет защитить развертку Lync Server 2013 от распространения наиболее распространенных форм вирусов с минимальными ухудшениями при взаимодействии с пользователями. Используйте Intelligent IM Filter, чтобы настроить фильтры для блокировки потенциально вредоносных мгновенных сообщений от неизвестных конечных точек за пределами корпоративного брандмауэра. Фильтры настраиваются путем задания критерия блокировки, например, можно блокировать сообщения содержащие гиперссылки с определенными префиксами и файлами с определенными расширениями.

Фильтр Intelligent IM предоставляет следующее:

  - Улучшенную фильтрацию URL-адресов.

  - Улучшенную фильтрацию при передаче файлов.

Настройка фильтра Intelligent IM:

  - Настройка URL-фильтра.

  - Настройка фильтра передачи файлов.

## Как параметры фильтрации применяются к мгновенным сообщениям

Перед разворачиванием инструмента Intelligent IM Message Filter следует понять как параметры фильтрации применяются при маршрутизации сообщений от одного сервера Lync Server 2013 к другому. Параметры фильтрации применяются последовательно, независимо от расположения серверов, будь то пределы одной организации или обмен данными между несколькими организациями. Данная последовательность отражается на вставку в сообщения специализированных уведомлений и предупреждений.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Фильтр мгновенных сообщений увеличивает нагрузку на ЦП при обработке URL-адресов в сообщении. Что отражается на производительности Lync Server.</td>
</tr>
</tbody>
</table>


На странице **URL-фильтр** группы **IM и присутствие** в панели управления Lync Server можно заблокировать все или некоторые гиперссылки, а также настроить выдачу предупреждения. Предупреждение вставляется в начало мгновенного сообщения, содержащего гиперссылку, если для настройки **Префикс гиперссылки** выбрать параметр **Отправлять предупреждающее сообщение**.

При передаче сообщения от одного сервера к другому, действуют следующие общие правила:

  - Если сервер блокирует сообщение (из-за установки флага **Блокировать URL-адреса с расширениями файлов** на странице **URL-фильтр** или из-за установки для опции **Префикс гиперссылки** параметра **Блокировать гиперссылки**), клиенту возвращается сообщение об ошибке. Последующие сервера не получают данное мгновенное сообщение.

  - Если сервер (Server1) добавляет предупреждение в мгновенное сообщение с активной гиперссылкой, то последующий сервер (Server2), получивший данное сообщение все еще может выполнить другое действие на основе присутствующей гиперссылки и заблокировать мгновенное сообщение или добавить свое предупреждение. Если Server2 настроен так, что добавляется предупреждение для данного типа URL-адреса, ранее добавленное Server1 предупреждение убирается и в начало сообщения добавляется предупреждение, заданное для Server2.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если Lync Server 2013 выполняется в смешанном окружении, то Live Communications Server 2005 с пакетом SP1 является минимальной версией, необходимой для использования приложения Intelligent IM Filter. Intelligent IM Filter не поддерживается в Live Communications Server 2005 без пакета SP1.</td>
</tr>
</tbody>
</table>


## Фильтрация URL-адресов

URL-адреса фильтруются по префиксам гиперссылок. Ниже приведены примеры подобных префиксов:

  - www\*.

  - ftp.

  - http:

Если не задать фильтр URL-адресов, то все адреса в мгновенных сообщениях проходят через сервер без изменений. Если фильтр задан, то адреса в мгновенных сообщения фильтруются согласно параметрам, заданным в диалоговом окне **Изменение URL-фильтра** и **Новый URL-фильтр**.

  - **Включить URL-фильтр**   Данный параметр включает фильтрацию URL-адресов для глобальной развертки или для выбранного сайта.

  - **Блокировать URL-адреса с расширениями файлов**   фильтр блокирует все активные интранет и Интернет-адреса, содержащие файл с расширением, из списка **Типы блокируемых расширений файлов** в окне **Изменение фильтра файлов**. При блокировке URL-адреса отправителю показывается сообщение об ошибке. Если выбран данный параметр, то он имеет приоритет над всеми другими параметрами фильтрации для каких-либо расширений файлов из списка **Типы блокируемых расширений файлов**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Фильтрация расширений проводится по стандартным названиям файлов. Фильтр может не работать с расширениями файлов, внедренных в другие имена.</td>
    </tr>
    </tbody>
    </table>


Чтобы настроить порядок обработки гиперссылок в обмене мгновенными сообщениями, выберите один из следующих параметров в настройке **Префикс гиперссылки**:

  - **Не фильтровать**   URL-адреса в сообщения отправляются через сервер. Если выбрать данный вариант, появится окно **Разрешить сообщение**. В окне **Разрешить сообщение** задайте уведомление, которое нужно вставлять в начало каждого сообщения с гиперссылкой. Данное уведомление не может содержать более 65535 символов.

  - **Блокировать гиперссылки**   Доставка сообщений с гиперссылками блокируется Lync Server, а отправителю показывается сообщение об ошибке.

  - **Отправлять предупреждение**   Lync Server разрешает использование активных гиперссылок в мгновенных сообщения, но добавляет предупреждение. Если выбрать данный вариант, то откроется окно **Предупреждение**. В окне **Предупреждение** необходимо ввести предупреждение, которое будет добавляться к мгновенным сообщениям с допустимыми гиперссылками. Например, это предупреждение может сообщать о потенциальной опасности открытия неизвестной ссылки, или напоминать о соответствующих требованиях и правилах вашей организации. Данное предупреждение не может содержать более 65535 символов.

Если выбрать параметр **Блокировать гиперссылки** или **Отправлять предупреждение**, то становятся доступны следующие опции:

  - **За исключение гиперссылок локальной интранет-сети**   фильтр блокирует только Интернет-ссылки. URL-адреса для местоположений внутри вашей интранет-сети проходят через сервер без изменений. Но URL-адреса интранет-сети, проходящие через отдельные сервера с Lync Server, зависят от типов локальных веб-сайтов, которые считаются частью интранет-зоны данных серверов. Чтобы проверить параметры интранет-зоны сервера см. описание процедуры “Как настроить параметры интранета в Internet Explorer” в разделе [Изменение фильтра URL-адресов по умолчанию](lync-server-2013-modify-the-default-url-filter.md).

  - **Фильтровать данные префиксы гиперссылок**   Чтобы выбрать блокируемые префиксы, нажмите **Выбрать** и затем в в поле **Выбор префикса гиперссылок** добавьте нужные к списку **Префиксы гиперссылок**.
    
    Все префиксы за исключением **href** должны завершаться точкой или двоеточием, или звездочкой с последующей точки. Допустимые префиксы могут содержать любой символы из набора допустимых для URL символов, за исключением символа звездочки(\*). Набор допустимых для URL символов таков: \#\*+/0123456789=@ABCDEFGHIJKLMNOPQRSTUVWXYZ^\_\` abcdefghijklmnopqrstuvwxyz|~

## Фильтрации передачи файлов

Фильтрация передачи файлов влияет и на мгновенные сообщения и на конференции. Для последних данные настройки влияют на функцию выдачи в клиенте Office Live Meeting 2007 и функции воспроизведения мультимедиа файлов.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server также предоставляет возможности фильтрации передачи файлов. Эти параметры на стороне сервера предоставляются в дополнение к элементам управления на стороне клиента, доступным в Lync Server.</td>
</tr>
</tbody>
</table>


Передачу файлов любых типов можно фильтровать во время обмена мгновенными сообщениям, при использовании функции выдачи в клиенте Office Live Meeting 2007 и во время воспроизведения мультимедиа файлов. Для контроля передачи файлов можно использовать следующие параметры:

  - **Включить фильтр файлов**   включается фильтрация файлов на глобальном уровне или для выбранного сайта.
    
    При включении фильтра, можно выбрать один из следующих вариантов в поле **Передача файлов**:
    
      - **Блокировать определенные типы файлов**   указываются фильтруемые сервером запросы на передачу файлов. Задается список блокируемых расширений. Элементы списка могут содержать все стандартные символы, кроме символа звездочки (\*). В клиенте Office Live Meeting 2007 функция выдачи остается включенной, на любой файл с данным расширением нельзя загружать и отправлять. Если установить флажок **Блокировать URL-адреса с расширением файла** на вкладке **URL-фильтр**, то URL-фильтр использует тот же список для блокировки активных гиперссылок, содержащих какое-либо из этих расширений. Чтобы выбрать блокируемые типы файлов, нажмите **Выбрать** и затем **Выбрать тип файла** и добавьте расширения к списку **Выбранные расширения типов файлов**.
    
      - **Блокировать все**   Сервер не пропускает мгновенные сообщения, содержащие запросы на передачу файлов и возвращает отправителю запрос сообщение об ошибке. Функция выдачи в клиенте Office Live Meeting 2007 отключается.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Фильтрация расширений файлов ограничиваются стандартными именами. Фильтр может не работать с расширениями, внедренными в другие названия.</td>
</tr>
</tbody>
</table>


## В данном подразделе

  - [Изменение фильтра передачи файлов по умолчанию](lync-server-2013-modify-the-default-file-transfer-filter.md)

  - [Создание нового фильтра передачи файлов для определенного сайта](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)

  - [Изменение фильтра URL-адресов по умолчанию](lync-server-2013-modify-the-default-url-filter.md)

  - [Создание нового фильтра URL-адресов для управления гиперссылками в сеансах обмена мгновенными сообщениями](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)

## См. также

#### Другие ресурсы

[Управление параметрами обмена мгновенными сообщениями и сведениями о присутствии в Lync Server 2013](lync-server-2013-managing-im-and-presence-settings.md)

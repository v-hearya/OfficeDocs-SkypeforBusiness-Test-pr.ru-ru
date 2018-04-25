﻿---
title: 'Lync Server 2013: определение требований к архивации'
TOCTitle: Определение требований организации к архивации
ms:assetid: ce0fc0f6-7704-4b80-bf19-a1fa9818fc7a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205276(v=OCS.15)
ms:contentKeyID: 49311184
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Определение требований к архивации в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-09_

Если ваша организация должна следовать нормативным правилам, вы можете развернуть службу архивирования для архивирования мгновенных сообщений и конференций Lync Server 2013. Дополнительные сведения о типе содержимого, который может быть архивирован см. в статье [Обзор архивации в Lync Server 2013](lync-server-2013-overview-of-archiving.md) документации по планированию.

Для реализации архивирования, сперва следует определить способ удовлетворения требований организации в плане архивирования. Для этого нужно определить следующее:

  - **Когда развертывать систему архивирования**. Систему можно развернуть как часть изначального развертывания Lync Server 2013, или же это можно сделать позже. Архивирование разворачивается с помощью топологий, добавляется в вашу топологию, которая затем публикуется.

  - **Следует ли архивировать внешние и внутренние коммуникации**. Можно включить архивирование внутренней корреспонденции (между внутренними пользователями), внешних (где участвует хотя бы один пользователь вне пределов вашей внутренней сети), или оба метода. Можно задать данные настройки для всей организации или для определенных узлов и пулов. По умолчанию, не задействован ни один из методов.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если для хранения архивированных данных применяется интеграция с Microsoft Exchange, настройки Exchange определяют архивируются ли сеансы связи Lync. Если в ваше развертывание входят несколько лесов, следует синхронизировать настройки между Lync Server и Exchange. Управление архивацией для внутренних и внешних коммуникаций доступно только для политики Lync. При использовании функции архивации, интегрированной с Exchange, выполняется или отменяется архивация обоих типов связи.</td>
    </tr>
    </tbody>
    </table>


  - **Для кого требуется архивирование**. Архивирование можно включить для всего развертывания на глобальному уровне или для отдельных узлов и пользователей. На каждом из этих уровней определяется что следует архивировать: сеансы обмена мгновенными сообщениями, конференции (встречи, с несколькими участниками) или оба вида корреспонденции. По умолчанию архивирование отключено.

  - **Насколько важно архивирование для пользователей в организации**. Если архивирование является очень важным для вашей организации, вы можете указать, чтобы Lync Server 2013 выполнялся в критическом режиме, при котором сессии обмена сообщениями и конференции блокировались при сбое службы архивирования. Пример:
    
      - Если служба архивирования временно не может отправить сообщение в очередь базы данных или вставить сообщение в базу, то функциональность развертки для отправки сообщений и проведения конференций блокируется до восстановлений функций по архивированию.
    
      - Если пользователь конференции отправляет файл, но файл не может быть скопирован в файловое хранилище архива, функциональность конференций блокируется до разрешения этой проблемы, а функциональность по отправке сообщений не блокируется.
    
    Данную настройку можно определить на глобальном уровне, уровне узла и пула. По умолчанию, критический режим не включен.

  - **Использовать ли интеграцию с Microsoft Exchange**. В данном случае хранилище архива интегрируются с хранилищем Exchange 2013, так что архивированные данные Lync Server и Exchange 2013 хранятся вместе в Exchange. Интеграцию с Microsoft Exchange можно использовать для хранения архивированных данных, которые размещаются в Exchange 2013, если их почтовые ящики находятся на судебном удержании. Если у вас нет развертывания Exchange 2013, интеграция не нужна или имеются пользователи Lync, не размещенные в Exchange 2013, вы можете развернуть отдельные базы данных архивирования с помощью SQL Server для хранения архивированных данных корреспонденции из Lync. Опцию интеграции с Microsoft Exchange можно определить на глобальном уровне, уровне узла или пула. По умолчанию интеграция с Microsoft Exchange отключена.

  - **Как будет происходить процесс управления архивированными данными**. База данных архива не предназначена для долгого хранения и в Lync Server 2013 нет функций по поиску в архивированных данных, поэтому их следует перемещать в другое хранилище. Lync Server предоставляет инструмент экспорта сессий для экспорта архивированных данных, которое создает расшифровки архивированных данных. Для каждой создаваемой глобальной политики, и для каждого политики узла и пользователя можно включить очистку данных и указать одну из следующих настроек:
    
      - Очистка экспортированных и хранимых архивированных данных через определенное количество дней. Минимальное количество дней равно одному. Максимальное – 2562 дней.
    
      - Очищать только экспортированные данные. При этом очищаются все записи, которые были экспортированы и помечены как допустимые к удалению в инструменте экспорта сессий.
    
    Данную опцию можно определить на глобальном уровне, уровне узла или пула. По умолчанию – отключена.

Управление архивацией осуществляется одним из следующих методов:

  - **Политики архивации**. Для включения или отключения архивирования внешней и внутренней корреспонденции можно использовать одну или несколько политик. По умолчанию архивирование отключено. Оно включается для вашей развертки с помощью глобальной политики. Можно указать несколько дополнительных политик для определенных узлов. Также можно указать политики для отдельных пользователей или их групп. Политики уровня пользователя переопределяют политики уровня узла, а те глобальные политики. Политики уровня пользователя реализуются только для отдельных пользователей, для которых заданы настройки по использованию политики. Конференции и групповые обмены сообщениями архивируются, только если включена политика архивирования по крайней мере для одного из участников.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если есть интеграция с Microsoft Exchange, то политики Exchange 2013 переопределяют политики архивирования Lync Server для всех пользователей, размещенных на серверах Exchange 2013.</td>
    </tr>
    </tbody>
    </table>


  - **Конфигурации архивирования**. Можно использовать одну или несколько конфигураций архивирования для указания большинства параметров, описанных выше, за исключением включения архивирования внешней и внутренней корреспонденции (что делается в политиках архивации). Конфигурации архивирования содержат глобальную конфигурацию по умолчанию и необязательные конфигурации узлов и пула. Глобальную конфигурацию удалить нельзя. Конфигурации уровня пула переопределяют конфигурации уровня узла. Те, в свою очередь, переопределяют глобальную конфигурацию.

В ходе анализа требований следует определить способ конфигурации глобальных параметров архивирования и глобальной политики. Также необходимо определиться с требованиями к конфигурациями и политиками уровня узлов, пулов и пользователей.

При разворачивании службы архивирования на пуле переднего плана или сервере Standard Edition, следует включить ее на всех других пулах переднего плана и серверах Standard Edition вашего развертывания. Это следует сделать, потому что пользователи, чью корреспонденцию требуется архивировать, могут быть приглашены в групповую переписку или конференции, размещаемую в другом пуле. Если архивирование в пуле, где размещается беседа или собрание, не включено, не будут архивированы все данные конференции. Архивирование будет по-прежнему может выполняться для пользователей, для которых включена эта функция, кроме того, будут архивироваться все мгновенные сообщения, но архивация содержимого конференций и событий не будет выполняться.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для делегации административных задач с поддержание стандартов безопасности вашей организации Lync Server 2013 использует контроль доступа на основе ролей(RBAC). С RBAC административные права выдаются пользователям при их назначении на предопределенные административные роли Чтобы настроить политики и конфигурации архивирования пользователь должен быть назначен на роль CsArchivingAdministrator (если конфигурация не выполняется прямо на сервере, где разворачивается служба архивирования, а не удалено с другого компьютера). Дополнительные сведения о RBAC см. в статье документации по планированию <a href="lync-server-2013-planning-for-role-based-access-control.md">Планирование контроля доступа на основе ролей в Lync Server 2013</a>. Список прав, разрешений и ролей пользователя, необходимых для развертывания архивирования см. в статье <a href="lync-server-2013-deployment-checklist-for-archiving.md">Контрольный список развертывания для архивации в Lync Server 2013</a>.<br />
Если применяется интеграция с Microsoft Exchange, для конфигурации политик Exchange требуются соответствующие административные права и разрешения. Дополнительные сведения см. в документации к Exchange 2013 .</td>
</tr>
</tbody>
</table>

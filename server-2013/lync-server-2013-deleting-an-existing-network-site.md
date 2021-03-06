﻿---
title: Удаление существующего сетевого узла
TOCTitle: Удаление существующего сетевого узла
ms:assetid: 2762149b-3572-4513-b838-beda7fa9e81e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ688001(v=OCS.15)
ms:contentKeyID: 49887909
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Удаление существующего сетевого узла

 

_**Дата изменения раздела:** 2012-11-01_

Сетевые сайты представляют собой офисы или расположения, заданные в рамках областей развертывания контроля допуска звонков (CAC) или расширения Enhanced 9-1-1. Можно использовать панель управления Lync Server 2013 для настройки сайтов и связывания их с регионами. Например, регион сети для Северной Америки может быть связан с сетевыми сайтами, такими как Chicago, Redmond и Vancouver. Сетевой сайт CAC должен быть создан для каждого сайта внутри организации, даже если для сайта отсутствуют ограничения пропускной способности. Используя панель управления Lync Server, можно создавать, изменять и удалять сетевые сайты. Используйте следующую процедуру для удаления существующего сетевого сайта. Дополнительные сведения о создании и изменении сетевых сайтов см. в статье [Создание или изменение сетевых узлов](lync-server-2013-creating-or-modifying-network-sites.md)

## Порядок удаления сетевого сайта

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Конфигурация сети**, затем **Сайт**.

4.  На странице **Сайт** выберите сайт, который требуется удалить.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Можно одновременно удалить несколько сайтов. Для этого нажмите клавишу CTRL и, удерживая ее, выберите несколько сайтов. Либо выберите все сайты, нажав <strong>Выбрать все</strong> в меню <strong>Изменить</strong>.</td>
    </tr>
    </tbody>
    </table>


5.  В меню **Изменить** щелкните **Удалить**.

6.  Нажмите кнопку **ОК**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Сетевой сайт нельзя удалить, если он связан с подсетью. При попытке удаления сайта, связанного с подсетью, появится сообщение об ошибке. Чтобы проверить, связан ли сайт с подсетями, щелкните сайт и выберите <strong>Подробнее</strong> в меню <strong>Изменить</strong>.</td>
    </tr>
    </tbody>
    </table>


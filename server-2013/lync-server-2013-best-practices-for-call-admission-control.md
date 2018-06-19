﻿---
title: 'Lync Server 2013: рекомендации по контролю допуска звонков'
TOCTitle: Рекомендации по контролю допуска звонков
ms:assetid: 97173cca-8175-4ae2-a247-eb7ef809da93
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398770(v=OCS.15)
ms:contentKeyID: 49310579
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Рекомендации по контролю допуска звонков в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-22_

Чтобы улучшить производительность и упростить развертывание, руководствуйтесь следующими рекомендациями при развертывании контроля допуска звонков:

  - Убедитесь, что глобальные сети соответствующим образом подготовлены для текущего и прогнозируемого трафика мультимедиа.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Мы рекомендуем учесть в ограничениях пропускной способности буфер. Существуют сценарии, такие как состояние гонки, которые затрагивают общую пропускную способность и могут привести к превышению предела пропускной способности. Например, при попытке запуска двух звонков в условиях приближения к пределу пропускной способности один из них может быть отклонен, так как другому удалось запуститься первым.</td>
    </tr>
    </tbody>
    </table>


  - Отслеживайте использование сети и записи регистрации вызовов, чтобы вы могли выбрать оптимальные параметры управления допуском звонков и обновлять их по мере изменения использования сети.

  - Используйте политики пропускной способности управления допуском звонков для настройки параметров качества обслуживания.

  - Если требуется перенаправлять заблокированные звонки в ТСОП, убедитесь в работоспособности и достаточной емкости этой телефонной сети. Дополнительные сведения см. в разделе [Планирование маршрутизации исходящей голосовой почты в Lync Server 2013](lync-server-2013-planning-outbound-voice-routing.md).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Под емкостью понимается количество портов, которые требуется открыть для обеспечения поддержки потенциального объема перенаправлений в ТСОП.</td>
    </tr>
    </tbody>
    </table>

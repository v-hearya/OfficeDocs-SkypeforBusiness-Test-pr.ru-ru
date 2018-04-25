﻿---
title: Настройка правил использования PIN-кодов для конференц-связи с телефонным подключением в Lync Server 2013
TOCTitle: Настройка правил использования PIN-кодов для конференц-связи с телефонным подключением в Lync Server 2013
ms:assetid: 27b79fb1-e2dc-4f71-bc82-b6eb61be2b16
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg520967(v=OCS.15)
ms:contentKeyID: 49309247
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка правил использования PIN-кодов для конференц-связи с телефонным подключением в Lync Server 2013

 

_**Дата изменения раздела:** 2012-06-19_

Пользователи Lync Server 2013, имеющие учетные данные доменных служб Active Directory (AD DS) в организации, могут присоединяться к конференциям с телефонным подключением как прошедшие проверку пользователи с помощью персонального идентификационного номера (ПИН-кода). Политика ПИН-кодов определяет способ работы ПИН-кодов для конференц-связи с телефонным подключением.

Чтобы применить особую политику к узлу или группе пользователей, вы можете создать новую политику ПИН-кодов. Если вы хотите применить одну и ту же политику ПИН-кодов ко всей организации, вы можете использовать глобальную политику ПИН-кодов, изменив ее так, как нужно. Политики ПИН-кодов применяются к пользователям в очередности от самой узкой области действия до самой широкой. Если вы назначили пользователю политику ПИН-кодов на уровне пользователя, ее параметры имеют приоритет. Если вы не назначили политику пользователя, применяется политика ПИН-кодов на уровне узла, если она определена. Если политики пользователя и узла не назначены, действуют параметры по умолчанию глобальной политики ПИН-кодов.

## Содержание

  - [Изменение параметров ПИН-кодов по умолчанию для конференц-связи с телефонным подключением в Lync Server 2013](lync-server-2013-modify-the-default-dial-in-conferencing-pin-settings.md)

  - [оздание или изменение параметров ПИН-кода для конференц-связи с телефонным подключением в Lync Server 2013 для сайта или группы пользователей](lync-server-2013-create-or-modify-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

  - [Удаление параметров ПИН-кода для конференц-связи с телефонным подключением для сайта или группы пользователей](lync-server-2013-delete-dial-in-conferencing-pin-settings-for-a-site-or-group-of-users.md)

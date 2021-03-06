﻿---
title: Требования для веб-конференций в Lync Server 2013
TOCTitle: Требования для веб-конференций в Lync Server 2013
ms:assetid: 125f847c-58ab-450f-ae43-41219fd38477
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ619171(v=OCS.15)
ms:contentKeyID: 49309003
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Требования для веб-конференций в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Если принято решение включить функции веб-конференций, должны быть спланированы следующие компоненты:

  -   
    Доступ к хранилищу файлов, которое используется для хранения содержимого веб-конференций.

  -   
    Интеграция с Сервер Office Web Apps, которая необходима для совместного использования файлов PowerPoint во время конференц-связи.

## Хранилище файлов

Во время проведения собраний службой веб-конференций Lync Server 2013 осуществляется хранение совместно используемого содержимого в хранилище файлов. В качестве части развертывания необходимо указать общий файловый ресурс, который будет использоваться как хранилище файлов или для сервера Standard Edition или для Enterprise Editionпереднего плана. Для хранилища файлов можно использовать существующий общий файловый ресурс или можно указать новый совместно используемый файловый ресурс, задав полное доменное имя файлового сервера, на котором будет находиться общий файловый ресурс, а также имя папки для этого нового файлового ресурса. Дополнительные сведения см. в разделе "Построитель топологии – определение файлового хранилища для клиентского сервера". Перед сохранением содержимого в хранилище файлов содержимое шифруется службой веб-конференций.

Сервером Lync Server 2013 поддерживается использование общих папок либо в системах хранения данных, напрямую подключаемых к серверу (DAS), либо в сети хранения данных (SAN), включая распределенную файловую систему (DFS), а также на избыточных массивах независимых дисков (RAID). После того как средством развертывания Lync Server определено местоположение общей папки, сервером Lync Server создается структура папок внутри общей папки:

  - 1-ApplicationServer-1

  - 1-CentralMgmt-1

  - 1-WebServices-1
    
      - CollabContent
    
      - CollabMetadata
    
      - DataConf

После этого содержимое, такое как слайды PowerPoint, доски, опросы и вложения, сохраняется службой веб-конференций в папках "CollabContent" и "CollabMetadata", расположенных в папке "WebServices".

Администратор должен установить разрешения для общей папки, чтобы RTC-группы обладали необходимыми правами на чтение и запись данных.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если обнаружены какие-либо ошибки, связанные с разрешениями, откройте построитель топологий, загрузите и повторно опубликуйте существующую топологию. При публикации топологии проверяются разрешения для общей папки, и при необходимости они сбрасываются в исходное состояние.</td>
</tr>
</tbody>
</table>


Для управления порядком хранения содержимого собраний можно использовать следующие параметры:

  - Параметром **ContentGracePeriod**, находящимся по адресу [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md), устанавливается продолжительность хранения содержимого веб-конференций на сервере после окончания собрания.

  - Параметром **MaxContentStorageMb**, находящимся по адресу [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md), задается максимальный объем файлового пространства, разрешенный для хранения содержимого во время одного собрания.

Параметром **MaxUploadFileSizeMb** не ограничивается настройка выгрузки файлов для Lync Web App. Предел на размер выгружаемого файла для Lync Web App устанавливается равным приблизительно 30 МБ и управляется файлом web.config служб IIS: /DataCollabWeb/Int\[Ext\]/Handler/web.config. Чтобы настроить предельный размер выгружаемого файла для Lync Web App, обновите `maxRequestLength` и `maxAllowedContentLength` в файле web.config, как показано ниже.

    <system.web>
        <!-- 
            Since this handler is used to upload files to DMCU the request size (in kilobytes) 
            has to fit max allowed file size uploaded by Lync Web App client.
            The timeout has to reflect the min client bandwidth. Timeout of 600 secs 
            and 512 Kbits of *client* bandwidth would result into aproximately 30 Mbytes 
            for Lync Web App upload size limit.
        -->
          <httpRuntime maxRequestLength="500000" executionTimeout="600" />
    
    
    
                    <security>
                    <requestFiltering>
                               <requestLimits maxAllowedContentLength="524288000" />
                    </requestFiltering>
                    </security>

Файл web.config необходимо обновить для каждого сервера переднего плана.

## Сервер Office Web Apps

Чтобы использовать эти новые возможности, администраторы должны установить Сервер Office Web Apps и настроить Lync Server 2013 для связи с Сервер Office Web Apps. В данной документации предоставляются сведения о порядке настройки Lync Server 2013 для работы с Сервер Office Web Apps. В этой документации отсутствует информация о порядке установки Сервер Office Web Apps. Сведения об установке см. на веб-сайте развертывания веб-приложений Microsoft Office по адресу <http://go.microsoft.com/fwlink/?linkid=257525>. В этом руководстве содержится полная информация по выполнению необходимых условий для Сервер Office Web Apps. Обратите внимание, что сервер Сервер Office Web Apps должен быть установлен на автономном компьютере, на котором не работает Lync Server, SQL Server или любое другое серверное приложение. (На этом компьютере не должна быть установлена какая-либо версия Office.) На любом компьютере, используемом для выполнения Сервер Office Web Apps, должен быть установлен определенный набор программного обеспечения (включая .NET Framework 4.5 и Windows PowerShell 3.0). Эти требования вместе со сведениями о настройке сертификатов и Службы IIS подробно рассматриваются на веб-сайте развертывания веб-приложений Microsoft Office по адресу <http://go.microsoft.com/fwlink/?linkid=257525>.

## См. также

#### Концепции

[Обзор веб-конференций в Lync Server 2013](lync-server-2013-web-conferencing-overview.md)  
[Контрольный список развертывания для веб-конференций](lync-server-2013-deployment-checklist-for-web-conferencing.md)


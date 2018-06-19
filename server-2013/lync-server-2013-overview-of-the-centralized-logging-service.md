﻿---
title: Обзор службы централизованного ведения журналов
TOCTitle: Обзор службы централизованного ведения журналов
ms:assetid: 975718a0-f3e3-404d-9453-6224e73bfdd0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ688145(v=OCS.15)
ms:contentKeyID: 49888097
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Обзор службы централизованного ведения журналов

 

_**Дата изменения раздела:** 2016-12-08_

Служба централизованная служба ведения журнала предоставляет средства для управляемого сбора данных в широкой или узкой области. Данные можно собирать одновременно со всех серверов в развертывании, можно определить конкретные элементы для трассировки, задать флаги трассировки и получать результаты поиска по одному компьютеру или по всем данным на всех серверах. Служба централизованная служба ведения журнала выполняется на всех серверах в развертывании. Архитектура централизованная служба ведения журнала состоит из следующих агентов и служб.

  - *Агент централизованной службы ведения журналов.*   ClsAgent.exe — это исполняемый процесс службы, который обменивается данными с контроллером и получает от него команды, заданные администратором. Агент выполняется в качестве службы на каждом компьютере Lync Server. Когда агент получает команду, он выполняет ее, отправляет сообщения на определенные компоненты для их трассировки и записывает журналы трассировки на диск. Он также считывает журналы трассировки на своем компьютере и отправляет данные трассировки на контроллер по запросу. Для получения команд ClsAgent прослушивает следующие порты: **TCP 50001**, **TCP 50002** и **TCP 50003**.

  - *Контроллер централизованной службы ведения журналов.*   ClsControllerLib.dll — это модуль выполнения команд для Командная консоль Lync Server и ClsController.exe. CLSControllerLib.dll отправляет агенту ClsAgent команды запуска, остановки, записи на диск и поиска. ClsControllerLib.dll объединяет журналы, полученные при выполнении команд поиска. Контроллер отвечает за отправку команд агентам, получение состояния этих команд, управление данными файла журнала поиска по мере их поступления от всех агентов со всех компьютеров из области поиска и объединение данных журналов в содержательный и упорядоченный набор выходных данных. В следующих разделах рассматривается использование Командная консоль Lync Server. ClsController.exe ограничен подмножеством возможностей и функций, доступных в Командная консоль Lync Server. Для получения справки по ClsController.exe введите команду `ClsController` в каталоге по умолчанию C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\ClsAgent.

**Взаимодействие ClsController и ClsAgent**

![Связь между CLSController и CLSAgent.](images/JJ688145.68c90811-5cf9-4a84-95b7-ea9ffc61eac4(OCS.15).jpg "Связь между CLSController и CLSAgent.")

Команды вводятся в интерфейсе командной строки Windows Server или с помощью Командная консоль Lync Server. Команды выполняются на компьютере, на котором выполнен вход в систему, и отправляются локальному агенту ClsAgent или на другие компьютеры и пулы в развертывании.

ClsAgent поддерживает файл индекса всех файлов .CACHE, которые имеются на локальном компьютере. ClsAgent размещает их так, чтобы они равномерно распределялись по томам, определенным параметром CacheFileLocalFolders, и не занимали более 80% места на каждом томе (расположение и процент локального кэша можно настроить с помощью командлета **Set-CsClsConfiguration**). ClsAgent также отвечает за удаление с локального компьютера устаревших кэшированных файлов журнала трассировки событий (файлов ETL). По истечении двухнедельного срока (этот временной интервал настраивается с помощью командлета **Set-CsClsConfiguration**) эти файлы копируются в общую папку и удаляются с локального компьютера. Дополнительные сведения см. в описании командлета [Set-CsClsConfiguration](set-csclsconfiguration.md). При получении запроса поиска условия поиска используются для выбора набора кэшированных ETL-файлов для выполнения поиска на основании значений из индекса, поддерживаемого агентом.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ClsAgent может выполнять поиск файлов, перемещенных в общую папку с локального компьютера. После перемещения файлов в общую папку ClsAgent не контролирует их устаревание и удаление. Необходимо определить административную задачу для отслеживания размера файлов в общей папке и их удаления или архивации.</td>
</tr>
</tbody>
</table>


Результирующие файлы журналов можно считывать и анализировать с помощью различных средств, в том числе с помощью **Snooper.exe** и других средств, способных считывать текстовые файлы, таких как **Notepad.exe**. Средство Snooper.exe входит в пакет средств отладки Lync Server 2013 и его можно загрузить из Интернета.

Подобно средству OCSLogger, служба централизованная служба ведения журнала имеет несколько компонентов, относительно которых можно выполнять трассировку, и предусматривает параметры для выбора флагов, таких как TF\_COMPONENT и TF\_DIAG. централизованная служба ведения журнала также сохраняет параметры уровня ведения журнала OCSLogger.

Важнейшим преимуществом Windows PowerShell по сравнению со средством командной строки ClsController является возможность настройки и определения новых сценариев с использованием выбранных поставщиков, предназначенных для конкретного пространства задач, настраиваемых флагов и уровней ведения журнала. Средство ClsController ограничено сценариями, определенными для исполняемого процесса.

В предыдущих версиях средство OCSLogger.exe позволяло администраторам и сотрудникам технической поддержки собирать файлы трассировки с компьютеров в развертывании. Наряду с преимуществами, средство OCSLogger обладало одним существенным недостатком. В заданный момент времени журналы можно было собирать только на одном компьютере. Можно было вести журналы на нескольких компьютерах с помощью отдельных копий OCSLogger, но при этом создавалось несколько журналов, а простого способа объединения результатов не существовало.

Когда пользователь запрашивает поиск журналов, ClsController определяет, на какие компьютеры отправить этот запрос (на основании выбранных сценариев). Контроллер также определяет, нужно ли выполнять поиск в общей папке, в которой находятся сохраненные ETL-файлы. При получении результатов поиска ClsController объединяет их в один упорядоченный по времени набор, который предоставляется пользователю. Пользователи могут сохранять результаты поиска на локальном компьютере для дальнейшего анализа.

При запуске сеанса ведения журнала пользователь указывает сценарии, имеющие отношение к решаемой задаче. В любой момент времени могут выполняться два сценария. Одним из этих сценариев должен быть сценарий AlwaysOn. Как можно понять из названия, этот сценарий должен всегда выполняться в развертывании, собирая сведения о всех компьютерах, пулах и компонентах.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Сценарий AlwaysOn не выполняется в развертывании по умолчанию. Этот сценарий необходимо явно запустить. После запуска он будет выполняться, пока не будет явно остановлен, а состояние выполнения будет сохраняться между перезагрузками компьютеров. Сведения о запуске и остановке сценариев см. в разделах <a href="lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md">Использование запуска службы централизованного ведения журнала для записи журналов</a> и <a href="lync-server-2013-using-stop-for-the-centralized-logging-service.md">Использование остановки службы централизованного ведения журналов</a>.</td>
</tr>
</tbody>
</table>


При возникновении неполадок запустите второй сценарий, связанный с обнаруженной проблемой. Воспроизведите условия возникновения проблемы и остановите ведение журнала для второго сценария. Выполните в журнале поиск данных, связанных с обнаруженной проблемой. При объединении журналов создается файл, содержащий сообщения трассировки со всех компьютеров в области сайта или в глобальной области развертывания. Если поиск возвращает слишком много данных, которые физически невозможно проанализировать (такую ситуацию часто называют отношением "сигнал-шум", в котором значение "шума" слишком велико), выполните другой поиск с более точными параметрами. На этом этапе можно заметить наборы данных, которые позволяют выявить признаки проблемы и сузить круг поиска. В конечном счете, после выполнения нескольких уточненных поисков можно обнаружить данные, имеющие отношение к проблеме, и определить ее причину.


> [!TIP]
> Если в Lync Server возникла проблемная ситуация, начните ее изучение с вопроса "что известно об этой проблеме?". Определение границ проблемы позволит исключить значительную часть рабочих объектов в Lync Server.<BR>Рассмотрим пример сценария, в котором пользователи не получают актуальные результаты при поиске контактов. Нет смысла искать проблемы в мультимедийных компонентах, корпоративной голосовой связи, конференц-связи и многих других компонентах. Неизвестно только то, где фактически возникла проблема: в клиенте или на стороне сервера? Контакты собираются из Active Directory репликатором пользовательских данных и передаются клиенту через сервер адресной книги (ABServer). ABServer получает обновления из базы данных RTC (куда их записывает репликатор пользовательских данных) и собирает их в файлы адресной книги, по умолчанию в 1:30. Клиенты Lync Server получают новую адресную книгу по случайному расписанию. Поскольку известно, как действует этот процесс, можно искать потенциальную причину среди проблем, связанных со сбором данных из Active Directory репликатором пользовательских данных, получением и созданием файлов адресной книги сервером ABServer или их загрузкой клиентами.


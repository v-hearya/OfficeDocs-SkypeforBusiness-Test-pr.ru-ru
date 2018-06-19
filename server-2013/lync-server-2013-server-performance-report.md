﻿---
title: 'Lync Server 2013: отчет о производительности сервера'
TOCTitle: Отчет о производительности сервера
ms:assetid: 942bb39a-1790-498e-9d99-8f6ce2d155c3
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg615018(v=OCS.15)
ms:contentKeyID: 49310558
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Отчет о производительности сервера в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

Отчет о производительности серверов содержит список серверов Microsoft Lync Server 2013, на которых был отмечен наивысший процент плохо обслуженных звонков. В отчете сервера распределены по типам, для каждого из них дается статистика следующих видов:

  - посредник

  - аудио- и видео конференций

  - Пограничный сервер аудио и видео

  - Шлюз (сервер-посредник)

  - Шлюз (в обход сервера-посредника)

  - Видео (включая показатели видео для серверов аудио и видеоконференций и соответствующих пограничных серверов)

  - Общий доступ к приложениям (включая показатели общего доступа для серверов аудио и видеоконференций и соответствующих пограничных серверов)

Следует помнить, что ранжирование в данном отчете относительное. Например, предположим что вашем наименее производительном сервере бывает один плохой звонок из 1 000. Это более чем приемлемый показатель в 0,1%. Но данный сервер (при учете того, что у других серверов этот процент еще меньше) все равно будет приведет в отчет о производительности серверов.

## Получение доступа к отчету о производительности серверов

Доступ к отчету можно получить с главный страницы отчетов по мониторингу. Отчет [Отчет по списку звонков в Lync Server 2013](lync-server-2013-call-list-report.md) можно детализировать, щелкнув один из следующих показателей:

  - Громкость вызова

  - Процент звонков низкого качества

Также можно детализировать отчет о тренде качестве среды передачи данных сервера, щелкнув один из следующих показателей:

  - Тренд

## Рекомендации по использовании отчета о производительности серверов

В отчете есть несколько фильтров данных. Например, можно фильтровать по типу сети (звонки по проводным и беспроводным соединениям) и типу доступа (звонки из-за пределов и изнутри брандмауэра). Рекомендуется использовать данные фильтры при просмотре отчета. Например, предположим что имеется сервер-посредник с процентом плохих звонков 3.24%. Если рассмотреть процент плохих беспроводных звонков, то процент может достигать значения 20%. Это значит, что на данном сервере возникают проблемы при обслуживании беспроводных звонков, эти сведения были скрыты, так как проблем при обслуживании проводных соединений не было.

## Фильтры

С помощью фильтров можно получить более точный набор данных и просмотреть полученные данные под другим углом. Например, в отчете о производительности серверов можно фильтровать данные по типу сети и серверу. Также можно выбрать способ группирования данных. В данном случае данные группируются по часам, дню, неделе и месяцу.

В следующей таблице приведены фильтры, которые можно использовать в отчете о производительности серверов.

### Фильтры отчета о производительности серверов

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>From</strong> (От)</p></td>
<td><p>Начальные дата/время для временного диапазона. Чтобы просмотреть данные по часам, введите начальные дату и время следующим образом:</p>
<p>7/7/2012 1:00 PM</p>
<p>Если вы не вводите начальное время, отчет автоматически начинается с 24:00 указанного дня. Чтобы просмотреть данные по дням, просто введите дату:</p>
<p>7/7/2012</p>
<p>Чтобы просмотреть данные за неделю или месяц, введите дату, выпадающую на любое время в рамках недели или месяца, которые вы хотите просмотреть (вам не требуется вводить первый день недели или месяца):</p>
<p>7/3/2012</p>
<p>Недели всегда отсчитываются с воскресенья по субботу.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong> (До)</p></td>
<td><p>Конечные дата/время для временного диапазона. Чтобы просмотреть данные по часам, введите конечные дату и время следующим образом:</p>
<p>7/7/2012 1:00 PM</p>
<p>Если вы не вводите конечное время, отчет автоматически заканчивается в 24:00 указанного дня. Чтобы просмотреть данные по дням, просто введите дату:</p>
<p>7/7/2012</p>
<p>Чтобы просмотреть данные за неделю или месяц, введите дату, выпадающую на любое время в рамках недели или месяца, которые вы хотите просмотреть (вам не требуется вводить первый день недели или месяца):</p>
<p>7/3/2012</p>
<p>Недели всегда отсчитываются с воскресенья по субботу.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Тип сервера</strong></p></td>
<td><p>Обозначает тип сервера, по которому дается сводка о производительности. Выберите один из следующих вариантов:</p>
<ol>
<li><p>[All] (Все)</p></li>
<li><p>посредник</p></li>
<li><p>аудио- и видео конференций</p></li>
<li><p>Пограничный сервер аудио и видео</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>Первые N</strong></p></td>
<td><p>Обозначает количество серверов (на основе их процента плохих звонков) для отображения в каждой категории. Например, если выбрать значение <strong>5</strong> , то отображается пять хуже всего справляющихся серверов. Выберите один из следующих вариантов:</p>
<ol>
<li><p>[All] (Все)</p></li>
<li><p>5</p></li>
<li><p>10</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><strong>Тип доступа</strong></p></td>
<td><p>Определяет, был ли клиент зарегистрирован во внутренней сети или внешней сети при выполнении вызова. Выберите один из следующих вариантов:</p>
<ol>
<li><p>[All] (Все)</p></li>
<li><p>Внутренняя</p></li>
<li><p>Внешняя</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p><strong>Тип сети</strong></p></td>
<td><p>Определяет тип сети, к которой был подключен клиент при выполнении вызова. Выберите один из следующих вариантов:</p>
<ol>
<li><p>[All] (Все)</p></li>
<li><p>Проводная</p></li>
<li><p>Беспроводная</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><strong>VPN</strong></p></td>
<td><p>Указывает, использовал ли внешний клиент подключение посредством виртуальной частной сети (VPN) при выполнении вызова. Выберите один из следующих вариантов:</p>
<ol>
<li><p>[All] (Все)</p></li>
<li><p>VPN</p></li>
<li><p>Не VPN</p></li>
</ol></td>
</tr>
</tbody>
</table>


## Показатели

В следующей таблице приведены сведения, предоставляемы в отчете о производительности серверов.

### Показатели отчета о производительности серверов: сводка по голосовым звонкам

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Можно проводить сортировку</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Сервер</strong></p></td>
<td><p>Нет</p></td>
<td><p>Название/IP-адрес сервера.</p></td>
</tr>
<tr class="even">
<td><p><strong>Громкость вызова</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество сделанных звонков.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Процент звонков низкого качества</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, классифицированных как звонки низкого качества. Звонок низкого качества – это любой звонок, хотя бы одна метрика которого превышает допустимое значение (например, звонок с чрезмерным дрожанием).</p></td>
</tr>
<tr class="even">
<td><p><strong>Круговой путь (мс)</strong></p></td>
<td><p>Да</p></td>
<td><p>Среднее время (в миллисекунда) требуемое для передачи пакета протокола транспорта реального времени (RTP) в другую конечную точку и обратно. Круговой путь в 100 и меньше миллисекунд считается допустимым.</p>
<p>Высокие значения времени двусторонней передачи могут быть обусловлены международной маршрутизацией вызовов, неправильной конфигурацией маршрутизации или перегрузкой сервера-посредника. Длительное время двусторонней передачи приводит к возникновению проблем при двусторонних аудиоразговорах в режиме реального времени.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Падение качества (средняя оценка)</strong></p></td>
<td><p>Да</p></td>
<td><p>Средняя экспертная оценка падения качества связи во время звонка. Значения лежат в диапазоне от 0.0 до 5.0. Значение 0.5 или меньшее обозначает допустимое падение качества. Изначально, средние оценки рассчитывались на основе оценок, даваемых звонкам пользователями по шкале от 1 до 5. В Lync Server сервер мониторинга использует набор алгоритмов для предсказания возможных оценок пользователей.</p>
<p>Большие оценки падения качества могут быть вызваны перегрузкой сети, недостатком пропускной способности, помехами в беспроводной среде, перегрузкой на сервере-посреднике или конечной точке. Падение качества приводит к искажению или потере аудиосигнала.</p></td>
</tr>
<tr class="even">
<td><p><strong>Потеря пакетов</strong></p></td>
<td><p>Да</p></td>
<td><p>Среднее значение потери RTP-пакетов. (Пакет считается потерянным, если он не дошел до назначения). Большие значения потери пакетов могут быть вызваны перегрузкой сети, недостатком пропускной способности, помехами в беспроводной среде, перегрузкой на сервере-посреднике. Обычно это приводит к искажению или потере аудиосигнала.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Дрожание (мс)</strong></p></td>
<td><p>Да</p></td>
<td><p>Среднее значение колебаний, зарегистрированных между прибытиями пакетов RTP. (Колебания – это показатель «вибрирования» вызова.) Высокие значения колебаний обычно вызваны перегрузкой сервера-посредника и приводят к искажению звука или потере аудиосигналов.</p></td>
</tr>
<tr class="even">
<td><p><strong>Степень маскированных аудиообразцов</strong></p></td>
<td><p>Да</p></td>
<td><p>Средняя степень маскированных аудиообразцов по отношению к общему числу образцов. (Маскирование аудио - это методика, которая применяется для сглаживания оборванной передачи, которая обычно происходит при потери сетевых пакетов). Большие значения обозначают частое применение данной методики, вызванной из-за потери пакетов или искажений сигнала.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Степень растянутых образцов</strong></p></td>
<td><p>Да</p></td>
<td><p>Средняя степень растянутых аудиообразцов по отношению к общему числу образцов. (Растягивание аудиопакета - это методика, которая применяется для поддержания качества звонка при обнаружении потери сетевого пакета). Большие значения обозначают частое применение данной методики, вызванное большими искажениями – аудиосигнал звучит как роботизированный.</p></td>
</tr>
<tr class="even">
<td><p><strong>Степень сжатых аудиообразцов</strong></p></td>
<td><p>Да</p></td>
<td><p>Средняя степень растянутых аудиообразцов по отношению к общему числу образцов. (Сжатие аудиопакета - это методика, которая применяется для поддержания качества звонка при обнаружении потери сетевого пакета). Большие значения обозначают частое применение данной методики, вызванное большими искажениями – аудиосигнал звучит как ускоренный или искаженный.</p></td>
</tr>
</tbody>
</table>


### Показатели отчета о производительности серверов: сводка по видеозвонкам

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Поддержка сортировки</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Тип звонка и конечной точки</strong></p></td>
<td><p>Нет</p></td>
<td><p>При щелчке этого элемента отчет предоставляет подробные сведения о звонках, основанных на этом типе. Типы звонков:</p>
<ul>
<li><p>Одноранговые звонки по объединенным коммуникациям</p></li>
<li><p>Сеансы конференц-связи по объединенным коммуникациям</p></li>
<li><p>Сеансы конференц-связи по ТСОП</p></li>
<li><p>Звонки по ТСОП: обходной канал передачи медиаданных</p></li>
<li><p>Звонки по ТСОП (без обхода): ветвь объединенных коммуникаций</p></li>
<li><p>Звонки по ТСОП (без обхода): ветвь шлюза</p></li>
<li><p>Другие типы звонков</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Громкость вызова</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков на тип звонка.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Процент звонков низкого качества</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, классифицированных как звонки низкого качества. Звонок низкого качества – это любой звонок, хотя бы одна метрика которого превышает допустимое значение (например, звонок с чрезмерным дрожанием).</p></td>
</tr>
<tr class="even">
<td><p><strong>Объем звонков (звонок по беспроводной сети)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, при которых используется беспроводное подключение.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Объем звонков (звонок по сети VPN)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, при которых используется подключение по сети VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>Объем звонков (внешний звонок)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Количество звонков, при которых используется внешнее подключение (то есть подключение за пределами внутренней сети).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Средняя скорость потока (кбит/с)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Средняя скорость видеопотока (кбит/с).</p></td>
</tr>
<tr class="even">
<td><p><strong>Процент низкой скорости потока</strong></p></td>
<td><p>Нет</p></td>
<td><p>Процент звонков с низкой скоростью потока.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Потеря исходящих пакетов</strong></p></td>
<td><p>Нет</p></td>
<td><p>Потеря исходящих пакетов RTP. Потеря пакетов происходит, когда пакеты протокола RTP, используемого для передачи аудио и видео через Интернет, не достигают точки назначения. Причиной высокого процента потерь может быть перегрузка сети, нехватка пропускной способности, радиопомехи беспроводной связи или перегрузка сервера мультимедиа. Потеря пакетов обычно приводит к искажению или пропаданию звука.</p></td>
</tr>
<tr class="even">
<td><p><strong>Процент остановленных кадров</strong></p></td>
<td><p>Нет</p></td>
<td><p>Процент &quot;остановленных&quot; кадров. При остановке кадров видео не воспроизводится, а звук продолжает воспроизводиться.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Средняя частота кадров исходящего сигнала</strong></p></td>
<td><p>Нет</p></td>
<td><p>Средняя частота кадров исходящей передачи во время вызова.</p></td>
</tr>
<tr class="even">
<td><p><strong>Средняя частота входящих кадров (%)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Средняя частота кадров входящей передачи во время вызова.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Низкая частота входящих кадров (%)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Процент звонков с низкой скоростью входящего видеопотока.</p></td>
</tr>
<tr class="even">
<td><p><strong>Работоспособность клиента (%)</strong></p></td>
<td><p></p></td>
<td><p>Показывает относительную работоспособность клиентского устройства во время вызова.</p></td>
</tr>
</tbody>
</table>


### Показатели отчета о производительности серверов: сводка по сеансам общего доступа к приложениям

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Поддержка сортировки</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Тип звонка и конечной точки</strong></p></td>
<td><p>Нет</p></td>
<td><p>При щелчке этого элемента отчет предоставляет подробные сведения о звонках, основанных на этом типе. Типы звонков:</p>
<ul>
<li><p>Одноранговые звонки по объединенным коммуникациям</p></li>
<li><p>Сеансы конференц-связи по объединенным коммуникациям</p></li>
<li><p>Сеансы конференц-связи по ТСОП</p></li>
<li><p>Звонки по ТСОП: обходной канал передачи медиаданных</p></li>
<li><p>Звонки по ТСОП (без обхода): ветвь объединенных коммуникаций</p></li>
<li><p>Звонки по ТСОП (без обхода): ветвь шлюза</p></li>
<li><p>Другие типы звонков</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Громкость вызова</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков на тип звонка.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Процент звонков низкого качества</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, классифицированных как звонки низкого качества. Звонок низкого качества – это любой звонок, хотя бы одна метрика которого превышает допустимое значение (например, звонок с чрезмерным дрожанием).</p></td>
</tr>
<tr class="even">
<td><p><strong>Объем звонков (звонок по беспроводной сети)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, при которых используется беспроводное подключение.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Объем звонков (звонок по сети VPN)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество звонков, при которых используется подключение по сети VPN.</p></td>
</tr>
<tr class="even">
<td><p><strong>Объем звонков (внешний звонок)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Количество звонков, при которых используется внешнее подключение (то есть подключение за пределами внутренней сети).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Дрожание (мс)</strong></p></td>
<td><p>Нет</p></td>
<td><p>Среднее значение колебаний, зарегистрированных между прибытиями пакетов RTP. (Колебания – это показатель «вибрирования» вызова.) Высокие значения колебаний обычно вызваны перегрузкой сервера-посредника и приводят к искажению звука или потере аудиосигналов.</p></td>
</tr>
<tr class="even">
<td><p><strong>Средняя относительная задержка в одну сторону</strong></p></td>
<td><p>Нет</p></td>
<td><p>Средняя относительная задержка в одну сторону между двумя конечными точками медиаданных. Это мера односкачковой задержки.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Средняя задержка обработки элемента RDP</strong></p></td>
<td><p>Нет</p></td>
<td><p>Среднее значение задержки обработки элементов RDP на сервере конференц-связи общего доступа к приложениям во время сеанса просмотра. Этот показатель не охватывает задержку передачи данных в сети. Высокое среднее значение отражает более длительную задержку при просмотре. На перегруженном сервере конференц-связи могут происходить в среднем более длительные задержки.</p></td>
</tr>
<tr class="even">
<td><p><strong>Процент испорченных элементов</strong></p></td>
<td><p>Нет</p></td>
<td><p>Итоговый процент испорченных элементов RDP.</p></td>
</tr>
</tbody>
</table>

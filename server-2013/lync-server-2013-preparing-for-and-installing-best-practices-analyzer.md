﻿---
title: Подготовка к установке анализатора соответствия рекомендациям
TOCTitle: Подготовка к установке анализатора соответствия рекомендациям
ms:assetid: 550613dd-dc08-482e-9980-a3fe187cd162
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg591347(v=OCS.15)
ms:contentKeyID: 49309805
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Подготовка к установке анализатора соответствия рекомендациям

 

_**Дата изменения раздела:** 2016-12-08_

Необходимо выполнить вход в систему как член группы администраторов, чтобы выполнить задачи, приведены в этом разделе.

## Системные требования для установки анализатора соответствия рекомендациям

Чтобы выполнить анализатор соответствия рекомендациям Lync Server 2013 для сканирования среды, на компьютере должна работать 64-разрядная версия одной из следующих операционных систем:

  - Windows Server 2008 R2 с пакетом обновления 1 (SP1) Standard

  - Windows Server 2008 R2 с пакетом обновления 1 (SP1) Enterprise

  - Windows Server 2008 R2 с пакетом обновления 1 (SP1) Datacenter

  - Windows Server 2012 Datacenter

  - Windows Server 2012 Standard

  - Windows Server 2012 Enterprise

  - ОС Windows Server 2012 R2 Datacenter

  - ОС Windows Server 2012 R2 Standard

  - ОС Windows Server 2012 R2 Enterprise

  - ОС Windows 8

  - ОС Windows 7

На компьютере также должны работать следующие компоненты:

  - Microsoft .NET Framework 4.5. Для Lync Server 2013 необходимо вручную установить на сервере 64-разр. версию Microsoft .NET Framework 4.5, прежде чем устанавливать Lync Server 2013.

  - Основные компоненты Lync Server 2013.

  - Пакет обратной совместимости WMI. Подробные сведения см. в разделе [Установка пакета обратной совместимости WMI](install-wmi-backward-compatibility-package.md) документации по миграции.

  - Windows PowerShell 3.0. Подробные сведения см. в разделе [Установка Windows PowerShell 3.0 для Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md) документации по развертыванию.

Можно установить анализатор соответствия рекомендациям на компьютерах с поддерживаемой ОС, где не работают основные компоненты Lync Server 2013 или пакет обратной совместимости WMI, однако на этих компьютерах анализатор можно будет использовать только для просмотра отчетов, но не для выполнения сканирования.

## Выбор компьютера для установки

Рекомендуется устанавливать анализатор соответствия рекомендациям Lync Server 2013 на компьютере, предназначенном для управления Lync Server 2013. Можно установить средство на сервере с Lync Server 2013 или на административном компьютере, на котором работают средства администрирования Lync Server 2013. Если установить средство на сервере с Lync Server, рекомендуется использовать это средство только для сканирования данного сервера.

## Установка анализатора соответствия рекомендациям

Анализатор соответствия рекомендациям можно загрузить для Lync Server 2013 с сайта [http://go.microsoft.com/fwlink/?linkid=266539\&clcid=0x419](http://go.microsoft.com/fwlink/?linkid=266539%26clcid=0x419).

Чтобы установить анализатор соответствия рекомендациям, запустите файл установщика Microsoft RtcBPA.msi на компьютере, где необходимо установить средство, затем следуйте инструкциям на экране. Местом установки программных файлов по умолчанию является *\<системный диск\>*\\Program Files\\Lync Server 2013\\BPA.


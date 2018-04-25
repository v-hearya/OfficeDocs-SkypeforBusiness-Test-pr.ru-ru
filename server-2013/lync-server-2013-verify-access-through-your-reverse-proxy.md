﻿---
title: 'Lync Server 2013: проверка доступа через обратный прокси-сервер'
TOCTitle: Проверка доступа через обратный прокси-сервер
ms:assetid: 3076a786-e022-4d41-91ec-1bf252b2a468
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg429697(v=OCS.15)
ms:contentKeyID: 49309354
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Проверка доступа через обратный прокси-сервер в Lync Server 2013

 

_**Дата изменения раздела:** 2013-03-29_

Используйте следующую процедуру, чтобы удостовериться, что пользователи могут получать доступ к информации на обратном прокси-сервере. Вам может потребоваться завершить настройку брандмауэра и DNS, чтобы обеспечить доступ к данным.

## Проверка доступа к веб-сайту через Интернет

  - Откройте браузер, введите в строке **адреса** URL-адреса, которые клиенты будут использовать для доступа к файлам адресной книги, и адрес веб-сайта для проведения конференций следующим образом:
    
      - Для сервера адресной книги введите URL-адрес, который выглядит следующим образом: **https:// *externalwebfarmFQDN* /ABS**, где *externalwebfarmFQDN* – это внешнее полное доменное имя внешних веб-служб, в которых размещаются службы адресной книги. Пользователь должен получить HTTP-запрос, поскольку безопасность каталогов в папке адресной книги настроена для использования проверки подлинности Windows по умолчанию.
    
      - Для конференций введите URL-адрес, который выглядит следующим образом: **https:// *externalwebfarmFQDN* /meet**, где *externalwebfarmFQDN* – это внешнее полное доменное имя фермы, в которой размещено содержимое собраний. Этот URL-адрес должен отображать страницу устранения неисправностей для конференций. Или же убедитесь, что простой URL-адрес для конференций работает правильно. В качестве примера простого URL-адреса для присоединения к конференции можно привести https://meet.contoso.com
    
      - Для расширения группы рассылки введите URL-адрес, который выглядит следующим образом: **https:// *externalwebfarmFQDN* /GroupExpansion/service.svc**. Пользователь должен получить HTTP-запрос, поскольку безопасность каталогов для службы расширения группы рассылки настроена для использования проверки подлинности Windows по умолчанию.
    
      - Для телефонного подключения введите URL-адрес, который выглядит следующим образом: **https:// *externalwebfarmFQDN* /dialin**, где *externalwebfarmFQDN* – это внешнее полное доменное имя веб-фермы, в которой размещается страница конференц-связи с телефонным подключением. Пользователь должен направляться на страницу конференц-связи с телефонным подключением. Или же убедитесь, что простой URL-адрес для конференций работает правильно. В качестве примера простого URL-адреса для присоединения к конференции можно привести https://dialin.contoso.com
    
      - Для проверки функционирования URL-адреса автообнаружения введите https://lyncdiscover. *Полное\_имя\_внешнего\_домена* . Браузер попросит вас открыть файл. Откройте его в блокноте. Типичный ответ должен иметь примерно следующий вид:
        
            {"AccessLocation":"External","Root":{"Links":[{"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/domain","token":"Domain"},
            {"href":"https:\/\/extweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/user","token":"User"},
            {"href":"https:\/\/lyncweb.contoso.com\/Autodiscover\/AutodiscoverService.svc\/root\/oauth\/user","token":"OAuth"}]}}

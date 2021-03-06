﻿---
title: Протоколы TLS и MTLS для Lync Server 2013
TOCTitle: Протоколы TLS и MTLS для Lync Server 2013
ms:assetid: b32a5b85-fc82-42dc-a9b2-96400f8cd2b8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn481133(v=OCS.15)
ms:contentKeyID: 59679356
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Протоколы TLS и MTLS для Lync Server 2013

 

_**Дата изменения раздела:** 2013-11-07_

Протоколы TLS и MTLS предоставляют зашифрованный обмен данными и проверку подлинности конечной точки в Интернете. Microsoft Lync Server 2013 использует эти два протокола для создания сети доверенных серверов и обеспечения шифрования всех сеансов обмена данными в Интернет. Весь обмен данными по протоколу SIP между серверами происходит по протоколу MTLS. Обмен данными по протоколу SIP от клиента к серверу выполняется по протоколу TLS.

Протокол TLS позволяет пользователям посредством их клиентского ПО выполнять проверку подлинности серверов Lync Server 2013, к которым они подключаются. При подключении по протоколу TLS клиент запрашивает от сервера действительный сертификат. Чтобы сертификат был действительным, он должен быть выдан ЦС, который также является доверенным объектом клиента, а имя DNS должно соответствовать имени сертификата. Если сертификат действительный, клиент использует открытый ключ в сертификате для шифрования симметричных ключей шифрования, которые будут использоваться для обмена данными, поэтому только исходный владелец сертификата может использовать закрытый ключ для шифрования содержимого сеанса обмена данными. Результатом является доверенное подключение, которое после этого уже не проверяется другими доверенными серверами или клиентами. В рамках этого контекста протокол SSL, используемый веб-службами, может быть связан как протокол на базе TLS.

Для подключений типа "сервер-сервер" используется протокол MTLS для взаимной проверки подлинности. В подключениях по протоколу MTLS создавший сообщение сервер и сервер, который получает его, обмениваются сертификатами из ЦС со взаимным доверием. Сертификаты подтверждают идентичность каждого из серверов с другим. В развертываниях Lync Server 2013 сертификаты, которые выданы корпоративным ЦС с действительным сроком действия и не отозваны, автоматически рассматриваются всеми внутренними клиентами и серверами как действительные, так как все члены домена Active Directory доверяют корпоративному ЦС с этом домене. В федеративных сценариях оба федеративных партнера должны доверять выдающему ЦС. Каждый партнер может использовать разные ЦС (при необходимости), пока другой партнер доверяет этому ЦС. Обеспечить это доверие легко, указав корневой сертификат ЦС партнера для пограничных серверов в их доверенных корневых ЦС или при использовании сторонних ЦС в качестве доверенных объектов обоих сторон.

Протоколы TLS и MTLS позволяют предотвратить прослушивание и атаки типа "злоумышленник в середине". В атаках типа "злоумышленник в середине" злоумышленник скрытым способом перенаправляет маршрут обмена данными между двумя объектами сети через свой компьютер. Протокол TLS и спецификация Lync Server 2013 доверенных серверов (только тех, которые указаны в топологий) частично устраняет риски атак типа "злоумышленник в середине" на уровне приложения посредством использования сквозного шифрования, управляемого с помощью криптографии открытого ключа между двумя конечными точками, поэтому злоумышленнику необходимо было бы иметь действительный и доверенный сертификат с соответствующим закрытым ключом, выданным от имени службы, с которой клиент взаимодействует с целью шифрования обмена данными. Тем не менее, необходимо следовать рекомендациям безопасности вашей сетевой инфраструктуры (в данном случае корпоративному DNS). Использование Lync Server 2013 предполагает, что сервер DNS является доверенным, как и контроллеры домена и глобальные каталоги, но DNS не обеспечивает уровень защиты от атак способом присоединения посередине (DNS hijack), запрещая серверу злоумышленника успешно давать ответ на запрос по поддельному имени.

На следующем рисунке показано высокоуровневое представление способа использования сервером Lync Server 2013 протокола MTLS для создания сети доверенных серверов.

**Доверенные подключения в сети Lync Server**

![Использование MTLS](images/Dn481133.437749da-c372-4f0d-ac72-ccfd5191696b(OCS.15).jpg "Использование MTLS")


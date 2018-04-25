﻿---
title: Test-CsRegistration
TOCTitle: Test-CsRegistration
ms:assetid: 9e38cb36-c97a-43f2-97fe-64759f663be2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412737(v=OCS.15)
ms:contentKeyID: 49310673
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsRegistration

 

_**Дата изменения раздела:** 2015-03-09_

Проверяет возможность входа пользователя в систему Lync Server. Командлет **Test-CsRegistration** является "искусственной транзакцией", т.е. имитацией типичных действий Lync Server, используемых для мониторинга работоспособности и производительности. Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    Test-CsRegistration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsRegistration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsRegistration [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Примеры

## ПРИМЕР 1

Пример 1 проверяет службу регистратора для пула atl-cs-001.litwareinc.com. Эта команда будет работать только в том случае, если тестовые пользователи определены для пула atl-cs-001.litwareinc.com. Если они определены, команда проверит, может ли первый пользователь выполнить вход в Lync Server.

Если тестовые пользователи не определены, команда завершится с ошибкой, потому что не сможет выполнить вход с использованием определенной учетной записи пользователя. Если для пула не определены тестовые пользователи, следует указать параметр UserSipAddress и учетные данные пользователя, с использованием которых команда будет выполнять попытки входа.

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com 

## ПРИМЕР 2

Команды, показанные в примере 2 проверяют возможность входа в систему Lync Server конкретного пользователя (litwareinc\\pilar). Для этого первая команда в примере использует командлет **Get-Credential**, чтобы создать объект учетных данных Windows PowerShell, содержащий имя и пароль пользователя Pilar Ackerman. (Так как имя входа litwareinc\\pilar включено в виде параметра, диалоговое окно запроса учетных данных Windows PowerShell потребует от администратора только ввести пароль учетной записи Pilar Ackerman.) Получившийся объект учетных данных затем будет сохранен в переменной с именем $cred1.

Вторая команда проверяет, может ли пользователь выполнить вход в пул atl-cs-001.litwareinc.com. Чтобы выполнить эту задачу, вызывается командлет **Test-CsRegistration** с тремя параметрами: TargetFqdn (полное доменное имя пула регистратора), UserCredential (объект Windows PowerShell, содержащий учетные данные пользователя Pilar Ackerman) и UserSipAddress (адрес SIP, соответствующий предоставленным учетным данным пользователя).

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:pilar@litwareinc.com"

## Подробное описание

Командлет **Test-CsRegistration** представляет собой пример "искусственной транзакции" Lync Server. Искусственные транзакции используются в Lync Server для проверки того, что пользователи смогут успешно выполнять обычные задачи, такие как вход в систему, обмен мгновенными сообщениями или звонок на телефон, находящийся в телефонной сети общего пользования (ТСОП). Эти тесты могут проводиться как вручную администратором, так и автоматически такими приложениями, как Microsoft System Center Operations Manager (ранее Microsoft Operations Manager).

Искусственные транзакции обычно выполняются двумя разными способами. Многие администраторы используют командлеты CsHealthMonitoringConfiguration для подготовки тестовых пользователей для каждого из пулов регистраторов. Данные тестовые пользователи — это пара пользователей, настроенных для использования в искусственных транзакциях (обычно это тестовые учетные записи, не принадлежащие настоящим пользователям). Подготовив тестовые учетные записи пользователей для пула, администраторы могут выполнить искусственную транзакцию для пула без необходимости указывать удостоверения (и учетные данные) учетных записей, задействованных в тесте.

Кроме того, администраторы могут выполнять искусственные транзакции с помощью учетных записей реальных пользователей. Например, если два пользователя не могут обмениваться мгновенными сообщениями, администратор может выполнить искусственную транзакцию с использованием учетных записей этих двух пользователей (вместо пары тестовых учетных записей), а затем попытаться найти и устранить проблему. При использовании реальных учетных записей для каждого из пользователей нужно будет указать имя для входа и пароль.

Командлет **Test-CsRegistration** позволяет убедиться в том, что пользователи в организации могут войти в Lync Server. Для выполнения этой проверки командлету **Test-CsRegistration** требуется одна тестовая учетная запись. Если вы настроили тестовых пользователей для пула, где будет проводиться проверка, то указывать учетную запись не требуется; командлет **Test-CsRegistration** будет автоматически использовать первую тестовую учетную запись, назначенную пулу. (Дополнительные сведения см. в разделе справки по командлету [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md).) Другой вариант проведения теста заключается в использовании учетной записи, которая не была назначена пулу. Это позволяет запустить тесты даже в том случае, если тестовые пользователи не настроены. Это также позволяет проверить возможность входа в Lync Server конкретного пользователя. (Если выбран этот подход, необходимо предоставить имя пользователя и пароль проверяемой учетной записи.)

Во время запуска командлета **Test-CsRegistration** он пытается выполнить вход от имени тестового пользователя в Lync Server и затем, в случае успешного входа, отключает тестового пользователя от системы. Все эти действия осуществляются без участия со стороны пользователя и не затрагивают реальных пользователей. Например, предположим, что тестовая учетная запись sip:kenmyer@litwareinc.com соответствует реальному пользователю с учетной записью Lync Server. В этом случае тест будет проводиться без какого-либо вмешательства в работу реального пользователя Ken Myer. Когда тестовая учетная запись Ken Myer выйдет из системы, личная учетная запись Ken Myer останется в системе.

Добавление параметра Verbose позволяет получить подробные сведения обо всех действиях, выполненных командлетом **Test-CsRegistration** для проведения теста.

Чтобы получить список всех ролей управления доступом на основе ролей (RBAC), которым назначен этот командлет (включая все самостоятельно созданные роли RBAC), выполните в командной строке Windows PowerShell следующую команду:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsRegistration"}

## Параметры


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Обязательный</th>
<th>Тип</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Обязательный</p></td>
<td><p>String</p></td>
<td><p>Полное доменное имя пула, который должен тестироваться.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Обязательный</p></td>
<td><p>PSCredential</p></td>
<td><p>Используйте объект учетных данных для тестируемой учетной записи. Значение, переданное параметру UserCredential, должно быть ссылкой на объект, полученной с помощью командлета <strong>Get-Credential</strong>. Например, следующий код возвращает объект учетных данных для пользователя litwareinc\kenmyer и сохраняет этот объект в переменной с именем</p>
<p>$x: $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>При запуске этой команды необходимо указать пароль пользователя. Данный параметр не требуется, если тест выполняется с параметрами конфигурации наблюдения за работоспособностью пула.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Необязательный</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
<td><p>Тип проверки подлинности, используемой в тесте. Разрешенные значения:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Необязательный</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Подавляет отображение любых сообщений о некритических ошибках, которые могут возникать при выполнении этой команды.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Необязательный</p></td>
<td><p>String</p></td>
<td><p>Если этот параметр используется, подробные результаты выполнения командлета будут сохранены в указанной переменной. Эта переменная включает в себя пару методов, ToHTML и ToXML, которые затем могут использоваться для сохранения этих результатов в HTML-файле или в XML-файле.</p>
<p>Для сохранения выходных результатов в переменной средства ведения журнала с именем $TestOutput используется следующий синтаксис:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Примечание. При указании имени переменной не следует добавлять в начало символ $. Чтобы сохранить информацию, содержащуюся в переменной средства ведения журнала, в HTML-файле, используйте команду, аналогичную следующей:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Чтобы сохранить информацию, содержащуюся в переменной средства ведения журнала, в XML-файле, используйте команду, аналогичную следующей:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Необязательный</p></td>
<td><p>String</p></td>
<td><p>При указании этого параметра подробные результаты выполнения командлета будут сохранены в указанной переменной. Например, чтобы сохранить результаты в переменную $TestOutput, используйте следующий синтаксис:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>При указании имени переменной, не добавляйте к его началу символ &quot;$&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Int32</p></td>
<td><p>Порт SIP, используемый службой регистратора. Этот параметр не обязателен, если регистратор использует порт по умолчанию, 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Необязательный</p></td>
<td><p>String</p></td>
<td><p>Адрес SIP для тестируемой учетной записи; например: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. Параметр UserSipAddress должен ссылаться на ту же учетную запись, что и параметр UserCredential. Данный параметр не требуется, если тест выполняется с параметрами конфигурации наблюдения за работоспособностью пула.</p></td>
</tr>
</tbody>
</table>


## Типы входных данных

Нет. Командлет **Test-CsRegistration** не принимает входные данные из конвейера.

## Типы возвращаемых данных

Командлет **Test-CsRegistration** возвращает экземпляр объекта Microsoft.Rtc.SyntheticTransactions.TaskOutput.

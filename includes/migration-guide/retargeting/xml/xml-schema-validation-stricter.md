### <a name="xml-schema-validation-is-stricter"></a>Более строгая проверка схемы XML

|   |   |
|---|---|
|Подробные сведения|В .NET Framework 4.5 проверка схемы XML является более строгой. При использовании xsd:anyURI для проверки URI, такого как протокол MailTo, при наличии пробелов в URI возникает сбой проверки. В предыдущих версиях .NET Framework проверка проходила успешно. Изменение затрагивает только приложения, предназначенные для .NET Framework 4.5.|
|Предложение|Если требуется менее строгая проверка .NET Framework 4.0, проверяющее приложение может быть ориентировано на версию 4.0 (или более раннюю) платформы .NET Framework. При изменении целевой платформы на .NET Framework 4.5 необходимо выполнить проверку кода и убедиться, что недопустимые URI (с пробелами) не ожидаются в качестве значений атрибута с типом данных anyURI.|
|Область|Дополнительный номер|
|Версия|4.5|
|Тип|Изменение целевой платформы|


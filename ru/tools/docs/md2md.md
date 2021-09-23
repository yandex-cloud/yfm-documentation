# Сборка в YFM

По умолчанию проект собирается в HTML, но вы можете настроить сборку в YFM. Для этого при выполнении команды `yfm` укажите ключ запуска `--output-format=md`.

Сборка в YFM позволяет использовать:
* [вставки](../../project/toc.md#includes) и [условия видимости разделов](../../project/toc.md#when) в файлах оглавлений;
* [условия отображения контента](../../syntax/vars.md#conditions) на страницах документа;
* [подстановки переменных](../../syntax/vars.md#subtitudes), если указан параметр `apply-presets`.

Используйте этот вид сборки, чтобы поддерживать несколько вариантов документации для разных пользователей. Например, если в документации есть разделы с внутренней информацией, вы можете держать два репозитория: приватный и публичный, и синхронизировать приватный в публичный с помощью условий. 
# Файл настроек

Проект может содержать файл настроек. По умолчанию, используется файл `.yfm` в корне проекта.

В файле конфигурации в yaml-формате описываются значения [параметров сборки](../tools/docs.md#settings).

```yaml
allowHTML: true
strict: true
varsPreset: "default"
ignore:
    "**/includes/*.md"
```

{% note tip %}

При запуске сборки можно указать путь до другого с помощью [параметра сборки](../tools/docs.md#settings) `--config`.

{% endnote %}

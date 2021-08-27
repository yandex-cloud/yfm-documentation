# Файл настроек

Настройки [трансформации YFM](../tools/transform/settings.md) и параметры сборки можно описать в файле настроек. По умолчанию, используется файл `.yfm` в корне проекта.

В файле конфигурации в yaml-формате описываются значения [параметров сборки](../tools/docs/settings.md).

```yaml
allowHTML: true
strict: true
varsPreset: "default"
ignore:
    "**/includes/*.md"
```

{% note tip %}

При запуске сборки можно указать путь до другого с помощью [параметра сборки](../tools/docs/settings.md) `--config`.

{% endnote %}

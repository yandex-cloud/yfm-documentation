# Использование дополнительных плагинов

## Подключение {#require}

### Если вы используете [Transformer](../tools/transform/index.md) {#transformer}

1. Установите npm пакет с нужным вам плагином, например, [markdown-it-emoji](https://www.npmjs.com/package/markdown-it-emoji).

   `npm i markdown-it-emoji`

2. Подключите его в своем коде.
3. Передайте массив необходимых плагинов в параметре `plugins`.

```javascript
const fs = require('fs');
const transform = require('@doc-tools/transform');
const cut = require('@doc-tools/transform/lib/plugins/cut');
const sup = require('@doc-tools/transform/lib/plugins/sup');
const emoji = require('markdown-it-emoji');

const content = fs.readFileSync(filePath, 'utf');

const {result: {html, meta}, logs} = transform(content, {plugins: [cut, sup, emoji]});
```

{% note warning %}

При передаче параметра `plugins` дефолтные плагины не подключаются. Если они вам нужны, то вам необходимо импортировать их из пакета `@doc-tools/transform` и передать в массиве подключаемых плагинов. Актуальный набор дефолтных плагинов вы всегда можете посмотреть в [этой документации](./default.md).

{% endnote %}

### Если вы используете [Builder](../tools/docs/index.md) {#builder}

1. Установите npm пакет с нужным вам плагином, например, [markdown-it-emoji](https://www.npmjs.com/package/markdown-it-emoji).
2. Переложите его в папку `./plugins` в пакете `@doc-tools/docs`.

Чтобы не делать это постоянно, вы можете собрать собственную сборку Builder. Для этого нужно скачать [исходники из GitHub](https://github.com/yandex-cloud/yfm-docs), подложить дополнительные плагины в папку `./plugins` и [собрать Builder](https://github.com/yandex-cloud/yfm-docs#installation-1).

## Передача параметров {#options}

YFM пробрасывает все неизвестные ему параметры из переданного объекта `options` во все плагины. Поэтому, если вам нужно передать какие-то параметры дополнительному плагину, то просто добавьте их в объект `options`.

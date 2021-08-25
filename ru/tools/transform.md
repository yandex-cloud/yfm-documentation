# Transformer

[@doc-tools/transform](https://www.npmjs.com/package/@doc-tools/transform) основной пакет YFM занимающийся трансформацией markdown в HTML.

Вы можете использовать его в своем коде, если вам нужно работать с YFM текстами во время работы программы. Например, отображать пользовательские сообщения или другой контент содержащий YFM.

## Установка и использование {#install}

1. Установите пакет

    `npm i @doc-tools/transform`

2. Подключите его в своем коде

    `const transform = require('@doc-tools/transform');`

3. И используйте как функцию, которая принимает на вход строку с markdown и настройки, а возвращает объект с результатом трансформации и логами.

    ```javascript
    const fs = require('fs');
    const transform = require('@doc-tools/transform');

    const content = fs.readFileSync(filePath, 'utf');
    const vars = { user: { name: 'Alice' } };

    const {
        result: {html, meta, title, headings},
        logs,
   } = transform(content, {vars});
    ```
   
4. Для корректного отображения подключите в проект

   стили
   ```css
   @import '~@doc-tools/transform/dist/css/yfm.css';
   ```
   
   и клиентские скрипты
   ```javascript
   import '@doc-tools/transform/dist/js/yfm';
   ```

## Настройки {#settings}

Имя | Описание | Тип | Значение по-умолчанию
:--- | :--- | :--- | :---
`vars` | [Переменные](../syntax.md#vars) | `Object` | `{}`
`plugins` | Используемые [плагины](../plugins/overview.md) | `function[]` | [см. в документации](../plugins/default)
`allowHTML` | Разрешено ли использование HTML | `bool` | `false`
`linkify` | Делать ли ссылками ссылкоподобные строки | `bool` | `false`
`breaks` | Переносить ли строки по символу перевода каретки | `bool` | `true`
`conditionsInCode` | Выполнять ли условия в блоках кода | `bool` | `false`
`disableLiquid` | Отключить [переменные](../syntax.md#vars) | `bool` | `false`
`supportGithubAnchors` | Генерировать дополнительные [якоря](../syntax.md#anchors) совместимые с GitHub (GFM) | `bool` | `false`
`highlightLangs` | Дополнительные языки для подсветки кода |  `{'lang': function}` | `{}`
`extractTitle` | Вернуть первый заголовок первого уровня в качестве заголовка всего документа | `bool` | `false`
`needTitle` | Вернуть первый заголовок первого уровня не удалив его из контента | `bool` | `false`
`lang` | Языка локализации дефолтных текстов | `string` | `ru`

## Возвращаемый объект {#returnObject}

`Transform` возвращает объект содержащий результат трансформации (поле `result`) и логи (поле `logs`).

### Результат {#result}

Объект результата содержит следующие поля:
1. `html` - строка с HTML.
2. `meta` - [мета-информации](../syntax.md#meta) из переданного контента.
3. `title` - заголовок документа, если указан параметр `extractTitle` или `needTitle`.
4. `headings` - список заголовков документа.

### Logs {#logs}

В логи записываются ошибки и предупреждения произошедшие при трансформации, а так же дополнительная информация о процессе трансформации. Логи разложены на три массива в зависимости от типа сообщения: `info`, `warn`, `error`.

## Подсветка кода {#highlightjs}

Для работы подсветки кода необходимо установить пакет [highlight.js](https://www.npmjs.com/package/highlight.js).

### Дополнительные языки для подсветки {#additionalLanguages}

Трансформер YFM использует `highlight.js` для подсветки языков. Вы можете передать дополнительный набор языков, который будет зарегистрирован для использования. Набор языков представляет собой объект, где ключ - это имя языка, а значение - функция, определяющая язык. Смотрите [уже существующие языки](https://github.com/highlightjs/highlight.js/tree/master/src/languages).

```javascript
const transform = require('@doc-tools/transform');
const customLang = require('./custom-lang');

const highlightLangs = { 'custom-lang': customLang };

const {result: {html, meta}, logs} = transform(content, {highlightLangs});
```
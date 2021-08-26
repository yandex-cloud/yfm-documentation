# Настройки

Настройки `transform` включают в себя [стандартные настройки YFM](../../settings.md), а также собственные настройки:

Имя | Описание | Тип | Значение по-умолчанию
:--- | :--- | :--- | :---
`plugins` | Используемые [плагины](../../plugins/overview.md) | `function[]` | [см. в документации](../../plugins/default)
`highlightLangs` | Дополнительные языки для подсветки кода |  `{'lang': function}` | `{}`
`extractTitle` | Вернуть первый заголовок первого уровня в качестве заголовка всего документа | `bool` | `false`
`needTitle` | Вернуть первый заголовок первого уровня не удалив его из контента | `bool` | `false`

## Подсветка кода {#highlightjs}

Для работы подсветки кода необходимо установить пакет [highlight.js](https://www.npmjs.com/package/highlight.js).

### Дополнительные языки для подсветки {#additionalLanguages}

Трансформер YFM использует `highlight.js` для подсветки языков. Вы можете передать дополнительный набор языков, который будет зарегистрирован для использования. Набор языков представляет собой объект, где ключ - это имя языка, а значение - функция, определяющая язык. Смотрите [уже существующие языки](https://github.com/highlightjs/highlight.js/tree/master/src/languages).

```javascript
const transform = require('@doc-tools/transform');
const customLang = require('./custom-lang');

const highlightLangs = { 'custom-lang': customLang };

const {result: {html, meta}, logs} = transform(content, {highlightLangs});

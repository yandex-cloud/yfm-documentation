# Transformer

[@doc-tools/transform](https://www.npmjs.com/package/@doc-tools/transform) основной пакет занимающийся трансформацией Yandex Flavored Markdown в HTML.

Вы можете использовать его в своем коде, если вам нужно работать с YFM текстами во время работы программы. Например, отображать пользовательские сообщения или другой контент содержащий YFM.

## Установка и использование {#install}

1. Установите пакет

    ```shell
    npm i @doc-tools/transform
    ```

3. Подключите его в своем коде

    ```javascript
    const transform = require('@doc-tools/transform');
   ```


4. И используйте как функцию, которая принимает на вход строку с YFM и [настройки](./settings.md), а возвращает объект с результатом трансформации и логами.

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

5. Для корректного отображения подключите в проект

   стили
   ```css
   @import '~@doc-tools/transform/dist/css/yfm.css';
   ```

   и клиентские скрипты
   ```javascript
   import '@doc-tools/transform/dist/js/yfm';
   ```

## Возвращаемый объект {#returnObject}

`Transform` возвращает объект содержащий результат трансформации (поле `result`) и логи (поле `logs`).

### Результат {#result}

Объект результата содержит следующие поля:
1. `html` - строка с HTML.
2. `meta` - [мета-информации](../../syntax.md#meta) из переданного контента.
3. `title` - заголовок документа, если указан параметр `extractTitle` или `needTitle`.
4. `headings` - список заголовков документа.

### Logs {#logs}

В логи записываются ошибки и предупреждения произошедшие при трансформации, а так же дополнительная информация о процессе трансформации. Логи разложены на три массива в зависимости от типа сообщения: `info`, `warn`, `error`.
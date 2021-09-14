# Подключить дополнительный плагин

YFM использует [markdown-it](https://www.npmjs.com/package/markdown-it) в качестве парсера, поэтому вы можете подключить любой плагин из [списка плагинов для markdown-it](https://www.npmjs.com/search?q=keywords:markdown-it-plugin).

## Подключение {#require}

{% list tabs %}

- Transformer

   1. Установите пакет с нужным плагином:    
      ```shell
      npm i <имя_плагина>
      ```

   1. Подключите плагин в своем коде, используя функцию `require()`:  
      ```javascript
      const plugin1 = require('<имя_плагина>');
      ```

   1. В параметре `plugins` добавьте новый плагин в массив:
      ```javascript
      const {result: {html, meta}, logs} = transform(content, {plugins: [<имя_плагина>]});
      ```
   {% note warning %}

   При переопределении параметра `plugins` необходимо заново подключать [плагины YFM](index.md). Для этого импортируйте их из пакета `@doc-tools/transform` и передайте в массиве плагинов. 

   {% endnote %}   

- Builder

   1. Установите пакет с нужным плагином:    
      ```shell
      npm i <имя_плагина>
      ```

   1. Перенесите его в папку `./plugins` в пакете `@doc-tools/docs`.

   {% note tip %}

   Чтобы не повторять эти действия перед каждой сборкой, соберите собственный Builder:
   * Установите исходный код с [GitHub](https://github.com/yandex-cloud/yfm-docs).
   * Перенесите дополнительные плагины в папку `./plugins`.
   * Соберите Builder по [инструкции с GitHub](https://github.com/yandex-cloud/yfm-docs#installation-1).

   {% endnote %}

{% endlist %}

## Передача параметров {#options}

YFM применяет неизвестные параметры из объекта `options` ко всем плагинам, поэтому для передачи параметров добавьте их в объект `options`.

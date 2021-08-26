# Builder

[@doc-tools/docs](https://www.npmjs.com/package/@doc-tools/docs) позволяет собрать полноценный документационный проект: с навигацией, внутренними переходами и полной поддержкой Yandex Flavored Markdown. Собранный проект представляет собой набор статических HTML, которые можно просмотреть локально или разместить на хостинге, в GitHub Pages или в [S3](https://cloud.yandex.ru/services/storage).

![Пример отображения страницы документации](../../../_images/leading.jpg)

## Установка {#install}

```shell
npm i @doc-tools/docs -g
```

## Использование {#use}

Пакет предоставляет команду `yfm` интерфейса командной строки. Для запуска обязательно нужно указать путь до файлов YFM и целевой путь сборки.

```shell script
yfm -i ./input-folder -o ./ouput-folder
```
# Yandex Flavored Markdown

**Yandex Flavored Markdown (YFM)** это диалект Markdown и набор инструментов от [трансформации YFM в HTML в рантайме](./tools/transform/index.md) до [сборки полноценного документационного проекта](./tools/docs/index.md).

- поддерживает [CommonMark Spec](https://spec.commonmark.org/) + свои расширения;
- [быстрый](https://www.npmjs.com/package/markdown-it#benchmark);
- [расширяемый](./plugins/overview.md): можно использовать [любые плагины markdown-it](https://www.npmjs.org/browse/keyword/markdown-it-plugin) или написать свои;
- безопасный из коробки: HTML экранируется;
- динамическая валидация;
- позволяет собрать документационный проект, например, как эта документация.

![Пример отображения страницы документации](./_images/overview_landing_white.jpg)

## Синтаксис {#syntax}

Синтаксис **Yandex Flavored Markdown (YFM)** базируется на [CommonMark Spec](https://spec.commonmark.org/), расширяя его дополнительными возможностями. Дополнительный синтаксис базируется на других популярных языках разметки и шаблонизаторах. Например, [liquid](https://shopify.github.io/liquid/) и [Pandoc](https://pandoc.org/).

Добавленные возможности:
 - [переменные: подстановка, условные операторы, циклы...](./syntax.md#vars):
 - [вкладки](./syntax.md#tabs);
 - [переиспользование контента](./syntax.md#includes)
 - [каты](./syntax.md#cuts)
 - [заметки](./syntax.md#notes)
 - [видео](./syntax.md#video)
 - [...](./syntax.md)

## Документационный проект {#project}

[Builder](./tools/docs/index.md) позволяет собрать полноценный документационный проект: с навигацией, внутренними переходами и полной поддержкой Yandex Flavored Markdown. Собранный проект представляет собой набор статических HTML, которые можно просмотреть локально или разместить на хостинге, в GitHub Pages или в [S3](https://cloud.yandex.ru/services/storage).

- темная тема и другие пользовательские настройки отображения;
    
    Попробуйте сами прямо сейчас в правом верхнем углу.

    ![user_settings](./_images/user_settings.jpg)

- [оглавление](./project/toc.md) по всему проекту и в рамках текущей страницы;
- [разводящие страницы](./project/leading-page.md);
- [переиспользуемый контент](./project/includes.md);
- [сборка в одностраничном виде](./tools/docs/singlePage.md);
- [выкладка на S3](./tools/docs/S3.md).

## В следующих сериях {#next}

- cтатический линтер;
- генераторы YFM из proto, openAPI, автогенеренной документации java, python, c++, go, etc.;
- лайки на страницах документации, они же индекс удовлетворенности пользователей (CSAT);
- автоматическая локальная пересборка при внесении изменений; 
- отображение контрибьюторов на страницах;
- бесплатный хостинг для open-source документационных проектов.

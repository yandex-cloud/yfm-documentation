# Оглавление документа

Структура документа описывается в файле `toc.yaml`. На основе этого файла генерируется оглавление и происходит сборка документации.

{% note warning %}

Файлы, которые не указаны в `toc.yaml`, не обрабатываются при сборке.

{% endnote %}

## Структура {#structure}

Стандартная структура файла `toc.yaml` имеет вид:

```yaml
title: Имя документа
href: index.yaml
items:
  - name: Имя раздела
    href: path/to/file.md
  - name: Имя группы разделов
    items:
      - name: Имя раздела
        href: path/to/file.md
      - name: Имя раздела
        href: path/to/file.md
  - name: Имя раздела
    href: path/to/file.md
```

* `title` — название документа. Отображается в оглавлении над списком всех разделов.
* `name` — имя раздела или группы разделов.
* `href` — относительный путь до файла.
* `items` — группирующий элемент.

## Условия видимости разделов {#when}

Отдельные разделы можно включать или не включать в документ в зависимости от значений [переменных](../syntax/vars.md). Для описания условий видимости используется параметр `when`.

Доступные операторы сравнения: `==`, `!=`, `<`, `>`, `<=`, `>=`.

```yaml
- name: Раздел с условным вхождением
  href: path/to/conditional/file.md
  when: version == 12
```

## Подстановки и условные операторы {#subtitudes}

Название документа поддерживает [подстановки](../syntax/vars#subtitudes) и [условные операторы](../syntax/vars#conditions).

```yaml
title: "{{ title }}"
```

{% note warning %}

Если значение начинается с подстановки, всегда заключайте его в кавычки. Без них значение обрабатывается как JSON, встроенный в YAML, что может привести к ошибкам сборки, например `TypeError: str.replace is not a function`.

{% endnote %}

## Вставки оглавлений {#includes}

Вы можете разбить оглавление на несколько файлов и вставить одно оглавление в другое. Когда это пригодится:
* У вас есть блоки оглавления, которые используются в нескольких документах.
* У вас большой документ, который проще собирать из нескольких блоков поменьше.

### Пример с включением оглавления как раздела {#include-as-section}

```yaml
- name: Имя заимствованного блока
  include:
    path: another/toc.yaml
```

По умолчанию в `path` указывается путь от корня документации. Имя импортируемого файла может быть любым, необязательно `toc.yaml`:

```yaml
- name: Инструкции для Android
  include:
    path: another/toc_android.yaml
```

### Пример с включением оглавления без создания раздела {#include-as-pages}

Также есть возможность включать `toc.yaml` с добавлением его элементов на тот же уровень оглавления.

`toc.yaml`:

```yaml
items:
  - name: Name1
    href: file1.md

  # Отсутствие поля name у элемента означает, что элементы включаемого оглавления стоит
  # добавлять на тот же уровень оглавления, а не как новый раздел
  - include: { path: path/to/toc.yaml }

  - name: NameX
    href: fileX.md
```
`path/to/toc.yaml`:

```yaml
items:
  - name: NameA
    href: fileA.md
  - name: NameB
    href: fileB.md
```
Результат в оглавлении:
- Name1
- NameA
- NameB
- NameX


### mode {#include-mode}

Есть несколько режимов, которые задаются в свойстве `mode`:

* `root_merge` — этот режим включен по умолчанию. В нём вместе с оглавлением скопируются и все используемые файлы и директории. Допустим, вы импортируете содержание из папки A в содержание, которое лежит в папке B. Тогда при сборке в папку B скопируются все файлы из папки A. Учтите, копирование происходит с перезаписью файлов.

  Так как при копировании меняется структура проекта, в метаданные новых файлов добавляется `sourcePath` с путем до исходного файла. Это поле используется для ссылки на редактирование страницы.
* `merge` — как `root_merge`, но путь к файлу с оглавлением указывается относительно текущего файла, в котором вы используете `include`.
* `link` — не изменяется структура проекта. Все ссылки включаемого оглавления меняются на ссылки относительно оглавления, в которое происходит включение.

Например, вы хотите указать относительный путь в `path` на оглавление, которое импортируете. Делайте так:

```yaml
items:
  - include: { mode: merge, path: ../relative/path/to/toc.yaml }
```

### Includers {#includers}

Доступно включение произвольного контента через `includers`, но только в случае если `includer` для этого типа контента имплементирован.

Возможные способы указания инклюдеров:

- массив `includer` объектов в поле `includers`

- `includer` объект в `includer` поле. _в процессе деприкации в пользу `includers` поля_

{% note warning "требования к include" %}

`include` должен иметь `path` куда контент будет включен

`path` поле должно быть **путем куда будет включен контент**.

`mode` должен быть **link или пропущенно, link является дефолтным поведением**

{% endnote %}

{% note warning "требования к includers" %}

`includers` должен быть массивом includer объектов, которые будут запущенны в указанном порядке

{% endnote %}

{% note warning "требования к includer" %}

параметры между инклюдер объектами разные, но одним обязательным параметром будет имя `includer`а.

`name` указывает имя инклюдера который запустится

{% endnote %}

#### Пример использования

Абстрактный пример использования инклюдеров

_смотри секцию соответствуещего инклюдера для конкретного примера использования_

```
# toc.yaml
...
items:
  - name: <item-name>
    include:
      path: <path-where-to-include>
      includers:
        - name: <name-of-the-first-includer>
          <includer-parameter>: <includer-parameter-value>
        - name: <name-of-the-second-includer>
        - name: <name-of-the-third-includer>
      mode: link
...
```

#### Список имплементированных инклюдеров

- [Generic](#includers-generic)
- [Open API](#includers-open-api)
- [Unarchive](#includers-unarchive)
- [Source Docs](#includers-source-docs) _в процессе деприкации в пользу generic инклюдера_

#### Generic {#includers-generic}

Вы можете сгенерировать документацию в markdown формате любой утилитой и включить её в основную документацию

Инклюдер сгенерирует по ней оглавление и включит контент в документацию

##### Пример использования

У нас есть проект документации в `doc_root` папке.

Положим сгенерированный контент в папку `doc_root/docs`.

Включим этот контент с помощью инклюдера в `doc_root/toc.yaml`.

Подключим разводящую в `doc_root/index.yaml`.

```yaml
# doc_root/toc.yaml
title: documentation
href: index.yaml
items:
  - name: docs
    include:
      path: docs
      includers:
        - name: generic
          input: docs
      mode: link
```

```yaml
# doc_root/index.yaml
title: documentation
links:
  - title: docs
    href: docs/
```

#### Open API {#includers-open-api}

Мы можем сгенерировать документацию из [Open API](https://www.openapis.org/) спецификации и включить её в основной документ

{% note warning %}

openapi инклюдер требует разрешение на использование HTML в документации

выставите `allowHTML` на `true` внутри `.yfm` конфигурации

```
allowHTML: true
```

{% endnote %}

##### Пример использования

У нас есть проект документации в `doc_root` папке.

Положим спецификацию open API по пути `doc_root/openapi.yaml`.

Теперь нам нужно включить её в `doc_root/toc.yaml` с помощью openapi инклюдера.

Подключим разводящую в `doc_root/index.yaml`.

```yaml
# doc_root/toc.yaml
title: documentation
href: index.yaml
items:
  - name: openapi
    include:
      path: openapi
      includers:
        - name: openapi
          input: openapi.yaml
      mode: link
```

```yaml
# doc_root/index.yaml
title: documentation
links:
  - title: openapi
    href: openapi/
```

#### Unarchive {#includers-unarchive}

Мы можем использовать `unarchive` инклюдер чтобы распаковать tarball перед тем как применять другие инклюдеры
к контенту внутри него, например `generic` инклюдер

##### Пример использования

Скажем у нас есть `docs.tar` в корне проекта по пути `doc_root/docs.tar`.

Внутри `docs.tar` находится контент который мы хотим включить используя `generic` инклюдер.

Тогда нам нужно применить цепь инклюдеров(`unarchive` -> `generic`) для достижения нащих целей.

```yaml
# doc_root/toc.yaml
title: documentation
href: index.yaml
items:
...
   - name: multiple
     include:
       path: multiple
       mode: link
       includers:
         # run unarchive includer
         - name: unarchive
           # specify tarball you want to unpack as input parameter
           input: docs.tar
           # specify output path where tarball content is going to be unpacked
           output: unpacked
         # run generic includer
         - name: generic
           # specify path from unarchive includers output field as input path
           input: unpacked
```

```yaml
# doc_root/index.yaml
title: documentation
links:
  - title: openapi
    href: openapi/
```

#### Source Docs

Мы можем включить документацию в формате [Source Docs](https://github.com/SourceDocs/SourceDocs) в основной документ.

{% note warning %}

Source Docs инклюдер находится в процессе деприкации в пользу [Generic Инклюдера](#includers-generic)

{% endnote %}

##### Пример использования

У нас есть проект документации в папке `doc_root`.

Положим результат исполнения Source Docs в папку `doc_root/docs`.

Включим его в документацию внутри `doc_root/toc.yaml`, указав `includer` sourcedocs.

Поставим ссылку на сгенерированную разводящую в основной в `doc_root/index.yaml`.

```yaml
# doc_root/toc.yaml
title: documentation
href: index.yaml
items:
  - name: docs
    include:
      path: docs
      includer: sourcedocs
      mode: link
```

```yaml
# doc_root/index.yaml
title: documentation
links:
  - title: docs
    href: docs/
```

## Настройка раскрытия разделов { #expanded }

По умолчанию все разделы оглавления свернуты, это можно настроить добавлением `expanded`:

```yaml
title: Yandex Cloud Marketplace
items:
  - name: Начало работы
    href: index.md
  - name: Тестовый топикхед
    expanded: true
    items:
      - name: Создание виртуальной машины
        href: create.md
  - name: Первичная настройка программного обеспечения
    href: setup.md
  - name: Работа с виртуальной машиной
    href: operate.md
  - name: Справочник API
    href: guide.md
```

Использовать `expanded` можно только для разделов первого уровня, указание `expanded` в разделах ниже - игнорируется.
Стоит использовать, чтобы важные разделы и страницы в оглавлении всегда были на виду.


## Скрытые разделы {#hidden}

Чтобы раздел был доступен только по прямой ссылке и не попал в оглавление, укажите параметр `hidden`.

```yaml
- title: Секретный документ
  href: secret.md
  hidden: true
```

Для полного исключения скрытых разделов из сборки используйте [ключ сборки](../tools/docs/settings.md) `--remove-hidden-toc-items=true`.

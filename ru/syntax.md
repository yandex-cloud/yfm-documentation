# Синтаксис

**Yandex Flavored Markdown (YFM)** является диалектом Markdown. Синтаксис базируется на [CommonMark Spec](https://spec.commonmark.org/), расширяя его дополнительными возможностями. Дополнительный синтаксис базируется на других популярных языках разметки и шаблонизаторах. Например, [liquid](https://shopify.github.io/liquid/) и [Pandoc](https://pandoc.org/).

## Заголовки {#headers}

Чтобы создать заголовок, используйте символ `#`.

В YFM используется 4 уровня заголовков. Заголовок страницы должен быть первого уровня. Для заголовков подразделов можно  использовать второй, третий и четвертый уровни.

```markdown
# Заголовок h1
## Заголовок h2
### Заголовок h3
#### Заголовок h4
```

{% cut "Результат" %}

# Заголовок h1
## Заголовок h2
### Заголовок h3
#### Заголовок h4

{% endcut %}

### Якоря {#anchors}

Для возможности ссылаться на заголовки документа, во время сборки для каждого заголовка формируется якорь. По умолчанию якорь — это текст заголовка, записанный в латинской транслитерации. Такой якорь изменится, если вы измените текст заголовка. Чтобы якорь не изменялся, укажите его в явном виде после заголовка. Вы можете указать несколько якорей одновременно.

```markdown
#### Заголовок h4
#### Заголовок h4 {#custom} {#header} {#custom-header}
```

{% cut "Результат" %}

#### Заголовок h4
#### Заголовок h4 {#custom} {#header} {#custom-header}

{% endcut %}

{% note tip "Совместимость с GitHub" %}

Если вам нужно, чтобы автоматически сгенерированные якоря совпадали с GitHub, например, кириллица не транслитирировалась, то можете включить в [настройках YFM](./tools/transform.md#settings) опцию `supportGithubAnchors: true`. Тогда  будут одновременно генерироваться два вида якорей: и в YFM, и в GitHub стиле.

{% endnote %}

## Параграфы {#paragraphs}

Для создания параграфа отделите пустой строкой один блок текста от другого.

```markdown
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna  aliqua.

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
```

{% cut "Результат" %}

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna  aliqua.

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

{% endcut %}

## Перенос строки {#breaks}

Для переноса строки просто начните новую строку.

```markdown
This is the first line.
And this is the second line.
```

{% cut "Результат" %}

This is the first line.
And this is the second line.

{% endcut %}

{% note tip "Настройка переноса строк" %}

Если вы привыкли к непереносу строк по переводу каретки в разметки, то можете выключить в [настройках YFM](./tools/transform.md#settings) опцию `breaks: false`. Тогда для переноса строк нужно будет ставить в конце строки два или более пробелов.

{% endnote %}

## Начертания {#emphasis} {#tracings}

### Полужирное {#strong} {#bold}

Чтобы задать для текста **полужирное** начертание, оберните его в двойные звездочки (`*`):

```markdown
I just love **bold text**.
```

{% cut "Результат" %}

I just love **bold text**.

{% endcut %}

### Курсив {#italic}

Для _курсивного_ начертание текста, оберните его в знаки подчеркивания:

```markdown
Italicized text is the _cat's meow_.
```

{% cut "Результат" %}

Italicized text is the _cat's meow_.

{% endcut %}

### Жирный курсив {#italic_bold}

Чтобы задать для текста _**полужирное и курсивное**_ начертание, оберните его одновременно в двойные звездочки и знаки подчеркивания:

```markdown
This text is **_really important_**.  
This text is _**really important**_.
```

{% cut "Результат" %}

This text is **_really important_**.  
This text is _**really important**_.

{% endcut %}

### Зачеркнутый текст {#strikethrough}

Для ~~зачеркнутого текст~~, напишите `~~` до и после текста:

```markdown
~~The world is flat.~~ We now know that the world is round.
```

{% cut "Результат" %}

~~The world is flat.~~ We now know that the world is round.

{% endcut %}

### Верхний регистр {#sup}

Для вывода символов в ^верхнем^ ^индексе^, их нужно обернуть в `^`:

```markdown
29^th^
```

{% cut "Результат" %}

29^th^

{% endcut %}

{% note warning %}

Внутри верхнего индекса не должно быть пробелов. Если вам нужно поднять несколько слов, то оберните каждое в `^`.

{% endnote %}

### Нижний регистр {#sub}

Для вывода символов в нижнем регистре, их нужно обернуть в `-`.

```markdown
H-2-O
```

{% note alert "Внешний плагин" %}

Синтаксис нижнего индекса не поддерживается YFM по-дефолту, но может быть добавлен с помощью стороннего плагина [markdown-it-sub](https://www.npmjs.com/package/markdown-it-sub). О том как использовать дополнительные плагины можно прочитать [тут](./plugins/import.md). Проголосовать за включение поддержки нижнего индекса по-умолчанию можно в [GitHub issue](https://github.com/yandex-cloud/yfm-transform/issues/70).

{% endnote %}

### Подчеркнутый текст {#underline}

Чтобы подчеркнуть текст оберните его с двух сторон `++`.

```markdown
++qwerty++
```

{% note alert "Внешний плагин" %}

Синтаксис подчеркнутого текста не поддерживается YFM по-дефолту, но может быть добавлен с помощью стороннего плагина [markdown-it-ins](https://www.npmjs.com/package/markdown-it-ins). О том как использовать дополнительные плагины можно прочитать [тут](./plugins/import.md). Проголосовать за включение поддержки нижнего индекса по-умолчанию можно в [GitHub issue](https://github.com/yandex-cloud/yfm-transform/issues/71).

{% endnote %}

## Цитаты {#blockquotes}

Цитату можно создать используя символ `>`.

Внутри цитаты можно использовать любой YFM синтаксис, но любые строки, даже пустые, нужно начинать с `>`.

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> ```bash
> echo 'Hello, World!'
> ```
```

{% cut "Результат" %}

> Dorothy followed her through many of the beautiful rooms in her castle.
> 
> ```bash
> echo 'Hello, World!'
> ```

{% endcut %}

### Вложенные цитаты {#nested_blockquotes}

Для вложенных цитат добавьте еще один символ `>`.

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

{% cut "Результат" %}

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

{% endcut %}

## Списки

### Упорядоченные списки {#ordered_list}

Для упорядоченного нумерованного списка используйте цифры с символом `.` или `)`. Рекомендованный формат  разметки: цифра `1` и символ `.`.

```markdown
#### List 1

1. First item
2. Second item
3. Third item

#### List 2

1. First item
1. Second item
1. Third item

#### List 3

1. First item
8. Second item
3. Third item
```

{% cut "Результат" %}

#### List 1

1. First item
2. Second item
3. Third item

#### List 2

1. First item
1. Second item
1. Third item

#### List 3

1. First item
8. Second item
3. Third item

{% endcut %}

### Неупорядоченный список {#unordered_list}

Чтобы оформить неупорядоченный маркированный список, используйте символы `*`, `-` или `+`. Рекомендуемый символ — `*`.

```markdown
* First item
* Second item
* Third item
```

{% cut "Результат" %}

* First item
* Second item
* Third item

{% endcut %}

{% note tip "Неупорядоченный список начинающийся с числа" %}

Если вам нужно начать неупорядоченный список с числа, то используйте обратный слеш `\` для эскейпинга.

```markdown
- 1968\. A great year!
- I think 1969 was second best.
```

{% cut "Результат" %}

- 1968\. A great year!
- I think 1969 was second best.

{% endcut %}

{% endnote %}

### Вложенные списки {#nested_lists}

Для создания вложенного списка добавьте отступ перед элементами дочернего списка. Допустимый размер отступа — от двух до пяти пробелов. Рекомендуемый размер отступа — четыре пробела.

```markdown
#### Упорядоченный список

1. Первый пункт
    1. Вложенный пункт
    1. Вложенный пункт
1. Второй пункт

#### Неупорядоченный список

* Элемент 1
   * Элемент A
   * Элемент B
* Элемент 2
```

{% cut "Результат" %}

#### Упорядоченный список

1. Первый пункт
    1. Вложенный пункт
    1. Вложенный пункт
1. Второй пункт

#### Неупорядоченный список

* Элемент 1
    * Элемент A
    * Элемент B
* Элемент 2

{% endcut %}

### Другие элементы в списках {#complex_lists}

В элементах списка можно использовать любой YFM синтаксис

```markdown
* First item
    ```bash
    echo 'Hello, World!'
    ```
* Second item
```

{% cut "Результат" %}

* First item
    ```bash
    echo 'Hello, World!'
    ```
* Second item

{% endcut %}

### Список определений {#def_list}

Для создания списка определений (`<dl>`) используйте символ `:`.

В описании определения можно использовать любой YFM синтаксис. Допустимы вложенные списки определений.

```markdown
Term 1

:   Definition 1

    Term 1.2

    :   Definition 1.2

Term 2 with *inline markup*

:   Definition 2

    * Можно использовать списки.
    * И **другую** разметку.

    ```bash
    echo 'Hello, world'!
    ```

    Third paragraph of definition 2.
```

{% cut "Результат" %}

Term 1

:   Definition 1

    Term 1.2

    :   Definition 1.2

Term 2 with *inline markup*

:   Definition 2

    * Можно использовать списки.
    * И **другую** разметку.

    ```bash
    echo 'Hello, world'!
    ```

    Third paragraph of definition 2.

{% endcut %}

## Вставка кода {#code}

Вы можете встроить фрагмент кода в текст абзаца или вынести его в отдельный блок.

### Фрагмент кода внутри текста {#inline-code}

Чтобы вставить фрагмент кода в текст, используйте символ `.

```markdown
At the command prompt, type `nano`.
```

{% cut "Результат" %}

At the command prompt, type `nano`.

{% endcut %}

{% note warning %}

Текст в инлайновом фрагменте кода не переносится, поэтому рекомендуется использовать не больше 100 символов. Если фрагмент кода больше, то лучше выделить его в отдельный блок.

{% endnote %}

### Фрагмент кода отдельным блоком {#codeblock}

Чтобы оформить фрагмент кода как отдельный блок, используйте утроенный символ `. Для подсветки синтаксиса укажите язык, на котором написан код.

{% note tip %}

В YFM можно передать [дополнительный язык подсветки](./tools/transform.md#additionalLanguages).

{% endnote %}

## Ссылки {#links}

Ссылки имеют вид  `[текст](ссылка)`, где:

* `[текст]` — текст ссылки.
* `(ссылка)` — URL или путь до файла, на который делается ссылка.

```markdown
My favorite search engine is [Yandex](https://yandex.com).

[ссылка на главную](./index.md)
```

{% cut "Результат" %}

My favorite search engine is [Yandex](https://yandex.com).

[ссылка на главную](./index.md)

{% endcut %}

### Ссылки с автоматической подстановкой текста из заголовка {#linkTitle}

В YFM вы можете добавлять ссылки на другие md-файлы без указания текста ссылки. Он подставится автоматически из заголовка указанного файла.

```markdown
[{#T}](./index.md)
```

{% cut "Результат" %}

[Yandex Flavored Markdown](./index.md)

{% endcut %}

### Пользовательский текст в тултипе на ссылке {#link_tooltip}

Вы можете добавить ссылке тултип со своим текстом.

```markdown
My favorite search engine is [Yandex](https://yandex.com "The best search engine").
```

{% cut "Результат" %}

My favorite search engine is [Yandex](https://yandex.com "The best search engine").

{% endcut %}

### URL и email

Email адреса и URL можно легко превратить в ссылку обернув их в `<>`.

```markdown
<https://www.markdownguide.org>
<fake@example.com>
```

{% cut "Результат" %}

<https://www.markdownguide.org>
<fake@example.com>

{% endcut %}

{% note tip "Начертания текста ссылки" %}

Начертание текста ссылки можно править аналогично обычному тексту.

```markdown
I love the **[Yandex Cloud](https://cloud.yandex.com)**.
This is the *[YFM Guide](https://yadocs.tech)*.
See the section on [`code`](#code).
Super [^men^](https://en.wikipedia.org/wiki/Major_Grom_(2017_film)).
```

{% cut "Результат" %}

I love the **[Yandex Cloud](https://cloud.yandex.com)**.
This is the *[YFM Guide](https://yadocs.tech)*.
See the section on [`code`](#code).
Super [^men^](https://en.wikipedia.org/wiki/Major_Grom_(2017_film)).

{% endcut %}

{% endnote %}

### Reference-style ссылки {#reference-style-links}

Вы можете сделать свои ссылки проще и читабельнее используя специальные reference-style ссылки. Такая ссылка состоит из двух частей: короткого описания в тексте и URL описанном в другом месте документа.

#### Форматирование первой части ссылки

Первая часть состоит из двух наборов квадратных скобок. В первой паре скобок, как и в обычной ссылке, указывается текст ссылки, а во втором - метка ссылки, по которой первая часть будет сопоставлена со второй. Метка может состоять из букв, цифр, пробелов и знаков пунктуации.

`[hobbit-hole][1]`

#### Форматирование второй части ссылки

Вторая часть ссылки из метки, URL и, опционально, текста для тултипа.

`[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle "Hobbit lifestyles"`

Вторая часть ссылки должна размещаться в том же YFM документе. Вы можете разместить ее после параграфа, где используется первая часть, или собрать все вторые части reference-style ссылок в конце документа.

#### Пример reference-style ссылки

```markdown
In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"
```

{% cut "Результат" %}

In a hole in the ground there lived a hobbit. Not a nasty, dirty, wet hole, filled with the ends
of worms and an oozy smell, nor yet a dry, bare, sandy hole with nothing in it to sit down on or to
eat: it was a [hobbit-hole][1], and that means comfort.

[1]: <https://en.wikipedia.org/wiki/Hobbit#Lifestyle> "Hobbit lifestyles"

{% endcut %}

## Изображения {#images}

Вставить изображение в документ можно с помощью разметки вида `![alt text](../_images/hello.jpg "Текст подсказки")`

Здесь:
* `[alt text]` —  альтернативный текст изображения;
* `../_images/hello.jpg` — путь или URL до файла изображения;
* `"Текст подсказки"` — текст подсказки при наведении указателя на изображение;

{% note warning %}

Изображения должны храниться в каталоге, имя которого начинается с символа `_`, иначе они будут удалены при сборке.

{% endnote %}

```markdown
![alt text](../_images/hello.jpg)
```

{% cut "Результат" %}

![alt text](../_images/hello.jpg)

{% endcut %}

### Размер изображения {#image-size}

Изображению можно задать размер в пикселях.

```markdown
![alt text](../_images/hello.jpg "Текст подсказки" =100x200)
```

{% cut "Результат" %}

![alt text](../_images/hello.jpg "Текст подсказки" =200x100)

{% endcut %}

### Изображение со ссылкой {#link-image}

Если завернуть изображение в ссылку, то получится кликабельное изображение.

```markdown
[![An old rock in the desert](../_images/mountain.jpg)](https://yandex.com/images/search?text=mountain)
```

{% cut "Результат" %}

[![An old rock in the desert](../_images/mountain.jpg)](https://yandex.com/images/search?text=mountain)

{% endcut %}

### Вставка через ссылку {#link_insert_image} {#link_insert}

Аналогично [reference-style ссылкам](#reference-style-links#), вы можете один раз объявить изображение в тексте документа, а затем вызывать его в тексте с помощью короткой ссылки.

1. Объявите изображение

   ```markdown
   [image]: ../_assets/image.png "Текст подсказки"
   ```

1. Вставьте изображение

   ```markdown
   ![alt text][image]
   ```

Такой способ может быть удобен, когда нужно вставить одно изображение несколько раз.

## Таблицы {#tables}

Таблицы состоят из строки с заголовками, разделительной строки и строк с данными.

Строка заголовков отделяется от ячеек таблицы тремя или более символами `-`. Колонки отделяются символами `|`.

```markdown
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```

{% cut "Результат" %}

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

{% endcut %}

### Выравнивание {#align-tables}

Текст в колонках можно выровнять по левому краю, правому краю или по центру добавлением символа `:` в строке отделяющей заголовок.

```markdown
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
```

{% cut "Результат" %}

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

{% endcut %}

### Другие элементы в таблицах {#complex-tables}

В ячейках таблицы можно использовать любые однострочные элементы: ссылки, однострочные блоки кода, различные начертания, изображения и т.д.

{% note tip "Генераторы таблиц" %}

Для создания таблиц вы можете воспользоваться различными [онлайн генераторами таблиц](https://www.tablesgenerator.com/markdown_tables).

{% endnote %}

## Заметки {#notes}

Заметка — это визуально выделенный блок, который позволяет привлечь внимание к определенному содержимому.

Существует 4 типа заметок: примечание (info), совет (tip), важно (warning) и внимание (alert).

{% note tip %}

Не следует часто использовать блоки заметок, так как они могут отвлекать пользователя от основного содержимого.
Также, хотя эти элементы могут содержать YFM, лучше не перегружать их, делая простыми и понятными.

{% endnote %}

### Примечание {#info}

```markdown
{% note info %}

Это примечание.

{% endnote %}
```

{% cut "Результат" %}

{% note info %}

Это примечание.

{% endnote %}

{% endcut %}

### Совет {#tip}

```markdown
{% note tip %}

Это совет.

{% endnote %}
```

{% cut "Результат" %}

{% note tip %}

Это совет.

{% endnote %}

{% endcut %}

### Важно {#warning}

```markdown
{% note warning %}

Это важная информация.

{% endnote %}
```

{% cut "Результат" %}

{% note warning %}

Это важная информация.

{% endnote %}

{% endcut %}

### Внимание {#alert}

```markdown
{% note alert %}

Это предупреждение.

{% endnote %}
```

{% cut "Результат" %}

{% note alert %}

Это предупреждение.

{% endnote %}

{% endcut %}

### Свой заголовок {#custom-title-note}

По умолчанию заметки имеют стандартный заголовок, но его можно переопределить:

```markdown
{% note info "Custom title" %}

Это важная информация.

{% endnote %}
```

{% cut "Результат" %}

{% note info "Custom title" %}

Это важная информация.

{% endnote %}

{% endcut %}

Если в кавычках ничего не указывать, у заметки не будет никакого заголовка:

```markdown
{% note info "" %}

Это важная информация.

{% endnote %}
```

{% cut "Результат" %}

{% note info "" %}

Это важная информация.

{% endnote %}

{% endcut %}

## Вкладки {#tabs}

Вы можете оформить текст в виде вкладок. Например, разделить инструкции для разных ОС.

Чтобы создать вкладки, оберните список в `{% list tabs %}` и `{% endlist %}`.

```markdown
{% list tabs %}

- Название таба1

  Контент таба1.

  * Можно использовать списки.
  * И **другую** разметку.

- Название таба2

  Контент таба2.

{% endlist %}
```

{% cut "Результат" %}

{% list tabs %}

- Название таба1

  Контент таба1.

    * Можно использовать списки.
    * И **другую** разметку.

- Название таба2

  Контент таба2.

{% endlist %}

{% endcut %}

{% note warning %}

При использовании вкладок обязательно оставлять пустые строки:

* Перед и после строк `{% list tabs %}` и `{% endlist %}`.
* Между текстом одной вкладки и заголовком следующей вкладки.

{% endnote %}

Внутри вкладок можно использовать YFM-разметку: списки, таблицы, изображения, код и т.д.

## Каты {#cuts}

Каты позволяют сворачивать контент ("убирать под кат"). Это можно использовать в длинных листингах, примерах кода и тд. Внутри катов можно использовать YFM.

Чтобы создать кат, используйте разметку вида:

```markdown
{% cut "Заголовок ката" %}

Контент который мы хотим скрыть

{% endcut %}
```

{% cut "Заголовок ката" %}

Контент который мы хотим скрыть

{% endcut %}

## Видео {#video}

Вы можете вставлять в страницу видео с наиболее популярных платформ.

```markdown
@[youtube](dQw4w9WgXcQ)
@[vimeo](19706846)
@[vine](etVpwB7uHlw)
@[prezi](1kkxdtlp4241)
```

Больше подробностей на [странице плагина](https://www.npmjs.com/package/markdown-it-video).

@[youtube](Pigvp8ixIXQ)

## Переменные {#vars}

В YFM вы можете объявлять и использовать переменные. При сборке переменные будут подставлены в текст документации или использованы для вычисления условий. Условия могут быть не только в тексте, но и в [оглавлении](./project/toc.md#when) или на [разводящей странице](./project/leading-page.md#when). Это удобно для сборки документации разных версий сервиса из одних и тех же исходных файлов или, например, можно унести в переменные часто повторяющие константы, такие как, названия продуктов.

Переменные можно передавать [при сборке документации](./tools/docs.md#settings) или описать в [файлах пресетов](./project/presets.md).

{% note tip "Отключить переменные" %}

Всю функциональность связанную с переменными можно выключить в [настройках YFM](./tools/transform.md#settings) с помощью опции `disableLiquid: true`.

{% endnote %}

### Подстановки {#substitudes}

Для вставки значения переменной в документ как текст, оберните ее название в двойные фигурные скобки

```markdown
Какой-то текст {{ variable-name-1 }} продолжение текста.
```

{% note tip %}

Если конструкция похожая на объявление переменной должна остаться как есть, то допишите перед ней `not_var_`.

```markdown
Какой-то текст not_var{{ variable-name-1 }} продолжение текста.
```

{% endnote %}

### Условные операторы {#conditions}

Вы можете включать в сборку документа тот или иной фрагмент текста в зависимости от значений переменных.

Например, чтобы собрать две версии документа для разных ОС:

```markdown
{% if  OS == 'iOS' %}

Скачайте приложение в [App Store](https://www.apple.com/ios/app-store/).

{% else %}

Скачайте приложение в [Google Play](https://play.google.com).

{% endif %}
```

{% note tip "Инлайновые условия" %}

Условные операторы могут применяться как к блокам, так и к отдельным частям инлайнового текста.

```markdown
Какой-то текст {% if  OS == 'iOS' %} Apple {% else %} Android {% endif %} продолжение текста.
```

{% endnote %}

### Циклы {#cycles}

Массивы в переменных можно обходить в циклах. Тогда контент внутри цикла будет вставлен в документ для каждого элемента цикла. Сам элемент доступен внутри этого контента как обычная переменная.

Цикл начинаться с `{% for user in users %}`, потом идет повторяемый контент и заканчивается `{% endfor %}`.

#### Примеры циклов

Переменные в [`presets.yaml`](./project/presets.md) для примеров ниже:

```yaml
default:
  users:
    - Alice
    - Mark
```

```markdown
Prefix {% for user in users %} {{user}} {% endfor %} Postfix

Prefix Alice Mark Postfix
```

```markdown
Prefix

{% for user in users %}

{{user}}

{% endfor %}

Postfix

Prefix
Alice
Mark
Postfix
```

```markdown
Prefix {% for user1 in users %} {% for user2 in users %} {{user1}}+{{user2}} {% endfor %} {% endfor %} Postfix

Prefix Alice+Alice Alice+Mark Mark+Alice Mark+Mark Postfix
```

### Функции {#functions}

Переменные в `presets.yaml` для примеров ниже:

```yaml
default:
  user:
    name: Pasha
```

#### slice

Поведение аналогично JavaScript методу [slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice).

```markdown
Hello M{{ user.name.slice(1) }}! => Hello Masha!
```

```markdown
Hello M{{ user.name.slice(1, 2) }}sha! => Hello Masha!
```

### Фильтры {#filters}

Переменные в [`presets.yaml`](./project/presets.md) для примеров ниже:

```yaml
default:
  user:
    name: alice
  users:
    - Alice
    - Mark
```

#### capitalize

Поднимает в верхний регистр первую встретившуюся букву в значении переменной.

```markdown
Hello {{ user.name | capitalize }}! => Hello Alice!
```

#### length

Вычисляет длину значения переменной.

```markdown
{{ users | length }} => 2

{{ user.name | length }} | length => 5
```

{% note warning %}

Перед и после оператора фильтра обязательно ставить пробел.

{% endnote %}

## Метаданные {#meta}

В начале файла можно добавить метаданные в формате yaml. Они вернутся после преобразования вместе с полученным HTML. В них, например, можно хранить информацию для SEO или авторов документа.

```yaml
---
title: Заголовок
description: Описание
---
```

## Переиспользование контента {#includes}

{% include [include](_includes/includes.md) %}

## Сноски {#footnotes}

Сноски позволяют добавить примечания и сноски не усложняя текст. Сноска состоит из блока примечания (текста или ссылки) и ссылки на него в тексте документа, которая отображается в верхнем индексе. Блок примечаний обычно размещается в конце документа, но может быть размещен где угодно.

```markdown
Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
```

{% note alert "Внешний плагин" %}

Синтаксис сносок не поддерживается YFM по-дефолту, но может быть добавлен с помощью стороннего плагина [markdown-it-footnote](https://www.npmjs.com/package/markdown-it-footnote). О том как использовать дополнительные плагины можно прочитать [тут](./plugins/import.md). Проголосовать за включение поддержки нижнего индекса по-умолчанию можно в [GitHub issue](https://github.com/yandex-cloud/yfm-transform/issues/72).

{% endnote %}

## Список задач {#task-list}

Список задач представляет из себя список чекбоксов.

Каждый пункт списка представляет из себя `- [ ] ` и какой-то текст. Если простановки галочки в чекбоксе поставьте `x` внутри квадратных скобок.

```markdown
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

{% note alert "Внешний плагин" %}

Синтаксис списка задач не поддерживается YFM по-дефолту, но может быть добавлен с помощью стороннего плагина [markdown-it-checkbox](https://www.npmjs.com/package/markdown-it-checkbox). О том как использовать дополнительные плагины можно прочитать [тут](./plugins/import.md). Проголосовать за включение поддержки нижнего индекса по-умолчанию можно в [GitHub issue](https://github.com/yandex-cloud/yfm-transform/issues/73).

{% endnote %}

## Формулы {#latex}

Для отображения формул можно использовать плагин [markdown-it-katex](https://www.npmjs.com/package/markdown-it-katex) или какой-то из его более [свежих форков](https://www.npmjs.com/search?q=markdown-it-katex).

{% cut "Примеры синтаксиса" %}

```latex
$\sqrt{3x-1}+(1+x)^2$
```

```latex
$$\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}$$
```

{% endcut %}

{% note alert "Внешний плагин" %}

Синтаксис формул не поддерживается YFM по-дефолту, но может быть добавлен с помощью стороннего плагина. О том как использовать дополнительные плагины можно прочитать [тут](./plugins/import.md).

{% endnote %}

## Экранирование служебных символов {#escaping}

Если необходимо, чтобы служебный символ разметки не был интерпретирован, то его можно экранировать обратным слешом `\`.

## HTML {#html}

По-умолчанию, YFM экранирует HTML. Если вы хотите все-равно его использовать, то вы можете выключить экранирование в [настройках YFM](./tools/transform.md#settings) с помощью опцию `allowHTML: true`.

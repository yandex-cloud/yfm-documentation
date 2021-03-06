# Пресеты переменных

Пресеты — наборы [переменных](../syntax/vars.md) с разными значениями.

Пресеты используются, чтобы поддерживать несколько вариантов документации из одних и тех же исходных файлов. Например, если документация содержит внутреннюю информацию, вы можете создать два пресета: `internal` и `external`, и вам не понадобится хранить значения переменных в файлах сборки.

Порядок работы с пресетами:
1. Опишите пресеты в файле `presets.yaml`.
1. При [сборке](../tools/docs/index.md) укажите название используемого пресета в параметре `varsPreset`.

## Структура {#structure}

Файл `presets.yaml` должен содержать пресет `default`. При вычислении переменных сначала учитываются значения, указанные в `default`. Затем на них накладываются значения из пресета, переданного при запуске сборки, так как он является приоритетным.

```yaml
default:
    position: Волшебник
internal:
    place: Изумрудный город
external:
    place: Страна Оз
```

## Иерархия файлов пресетов {#hierarchy }

Вы можете использовать несколько файлов пресетов. При вычислении переменных более приоритетными будут те, которые находятся ближе к конвертируемому файлу.

{% note tip %}

Рекомендуется использовать верхнеуровневые пресеты: наиболее близкие к корню проекта.

{% endnote %}

#### Пример

```
input-folder
|-- .yfm
|-- toc.yaml
|-- presets.yaml // 2
|-- index.yaml
|-- quickstart.md
|-- pages
    |-- presets.yaml // 1
    |-- faq.md
    |-- how-to.md
```

* При сборке файла `faq.md` значения переменных, объявленные в файле 1, будут иметь приоритет над файлом 2.
* При сборке файла `quickstart.md` будут учитываться только значения переменных, объявленные в файле 2.

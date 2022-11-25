# Перевод

`yfm translate` переводит вашу документацию используя [Yandex Translator](https://cloud.yandex.ru/docs/translate/)

## Настройка

- получите OAUTH токен как описано в [yandex.cloud документации](https://cloud.yandex.ru/docs/iam/concepts/authorization/oauth-token)

- положите его в `.ya_oauth_token` файл внутри домашней директории или укажите с помощью `YANDEX_OAUTH_TOKEN` переменной окружения

- получите идентификатор каталога на который у вашего аккаунта есть роль editor или выше как описано в [yandex.cloud документации](https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id)

- выставить поле `yandexCloudTranslateFolderId` внутри `.yfm` файла конфигурации значением идентификатора из предыдущего пункта

- выставить поле `yandexCloudTranslateGlossaryPairs` внутри `.yfm` файла конфигурации если вам требуется использование glossary словаря

```
# glossary example

yandexCloudTranslateGlossaryPairs:
    - { sourceText: InstreamAdBreakPositionType, translatedText: InstreamAdBreakPositionType }
```

_Это позволит **InstreamAdBreakPositionType** остаться без изменения в тексте_

Теперь вы можете использовать `yfm` для перевода вашей документации

## Опции

| Название Опции    | Обязательна | значение         | описание                                                                     |
| ----------------- | ----------- | ---------------- | ---------------------------------------------------------------------------- |
| --input           | да          | путь             | путь до входной документации                                                 |
| --output          | да          | путь             | путь до выходной документации                                                |
| --source-language | да          | код языка        | код языка в [ISO 639-1 формате](https://en.wikipedia.org/wiki/ISO_639-1)     |
| --target-language | да          | код языка        | код языка в [ISO 639-1 формате](https://en.wikipedia.org/wiki/ISO_639-1)     |

## Использование

```
yfm translate --input input_folder --output output_folder --source-language ru --target-language en
```

_Это переведёт вашу русскую документацию в **input_folder** на английскую, которая будет расположенна в **output_folder**_

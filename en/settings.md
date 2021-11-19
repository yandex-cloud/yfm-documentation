# Settings

Standard YFM settings are listed below. Depending on the tool you use, you can configure them in one of the following ways:

* In a [configuration file](./project/config.md).
* As a function parameter ([Transformer](./tools/transform/index.md)).
* Via startup keys ([Builder](./tools/docs/index.md)).

| Name | Description | Type | Default value |
| :--- | :--- | :--- | :--- |
| `vars` | [Variables](./syntax/vars.md) | `Object` | `{}` |
| `allowHTML` | Allow HTML | `bool` | `false` |
| `linkify` | Convert link-like strings to links | `bool` | `false` |
| `breaks` | Use the carriage return character for a line break | `bool` | `true` |
| `conditionsInCode` | Meet conditions in code blocks | `bool` | `false` |
| `disableLiquid` | Disable the use of variables | `bool` | `false` |
| `supportGithubAnchors` | Generate additional [anchors](./syntax/base.md#headers) that are compatible with GitHub | `bool` | `false` |
| `lang` | Localization language of default texts | `string` | `ru` |


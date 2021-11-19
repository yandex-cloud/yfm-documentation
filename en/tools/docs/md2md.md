# Building a project in YFM

By default, the project is built in HTML, but you can choose to build it in YFM. To do this, when executing the `yfm` command, specify the startup key `--output-format=md`.

Building in YFM allows you to use:

* [Inserts](../../project/toc.md#includes) and [section visibility conditions](../../project/toc.md#when) in tables of contents files.
* [Content visibility conditions](../../syntax/vars.md#conditions) on document pages.
* [Variable substitutions](../../syntax/vars.md#subtitudes) if the `apply-presets` parameter is specified.

Use this type of build to support multiple document versions for different users. For example, if there are sections with internal information in the documentation, you can keep two repositories: private and public, and synchronize private with public using conditions.


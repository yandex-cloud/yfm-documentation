# Builder

[@doc-tools/docs](https://www.npmjs.com/package/@doc-tools/docs) is a package for building a documentation project with navigation, internal transitions, and full support for Yandex Flavored Markdown.

A built project is a set of static HTML files that can be viewed locally or on a host, in GitHub Pages, or in [S3](publish-s3.md).

## Installation {#install}

To install the package, run this command:

```shell
npm i @doc-tools/docs -g
```

## Usage {#use}

The package provides the `yfm` CLI command.

To start rendering, run the command specifying the required [startup keys](settings.md):

* `--input, -i`: The path to the project folder.
* `--output, -o`: The path to the folder for output data (static HTMLs).

```shell script
yfm -i ./input-folder -o ./ouput-folder
```


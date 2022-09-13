# Revision history

## September 2022

### yfm-docs

#### 1.26.0

- services/leading: add [substitutions and conditional operators support](./project/leading-page.md#subtitudes) in document title and description
- services/tocs: add [substitutions and conditional operators support](./project/toc.md#subtitudes) in document title

#### 1.24.0

- includers/openapi: allows autogeneration from openapi specification and inclusion into the main document
  [Open API](./project/toc.md#open-api)

### yfm-transform

#### 2.12.0

- Functionality to [set image size](./syntax/media.md) enabled by default.

## July 2022

### yfm-docs

#### 1.23.0

- include/includers: allows 3rd party generated content integration into documentation.
- include/includers/sourcedocs: allows you to integrate sourcedocs generated document into yfm documentation.
  [Includers](./project/toc.md#includers)

## June 2022

### yfm-transform

#### 2.8.0

- Spaces inside inline conditions are not deleted

#### 2.7.0

- Single-page logic has been removed from the plugins (temporarily reverted in version 2.8.2)

## May 2022

### yfm-transform

#### 2.6.0

- Added plugin for [task lists syntax](./syntax/additional.md#tasks-list)

## April 2022

### yfm-docs

#### 1.22.0

- Support filtering of the title and title of the meta on the leading page (index.yaml)
- Support filtering of the title on the contents (toc.yaml)

#### 1.21.0

- Supported using of symlinks with a relative path

## March 2022

### yfm-docs

#### 1.20.0

- Supported filtering of the description on the leading page (index.yaml)

#### 1.19.0

- The linter runs in parallel with the build
- The arguments `--link-disabled`, `--build-disabled` and `--add-map-file` are supported, by default they have the value `false`.
  [Read more](tools/docs/settings.md)

### yfm-transform

#### 2.5.0

- Rewritten in Typescript

## December 2021

### yfm-docs

#### 1.18.0

Update YFM to v2.4. Added support [monospaced text](./syntax/base.md) and [multiline tables](./syntax/tables/multiline.md).

#### 1.17.0

* After pre-processing the documentation (with output-format=md), we do not remove not_var from the syntax similar to variables.
  [Substitutions](./syntax/vars.md#subtitudes)

#### 1.16.0

* Added modes for including toc: `root_merge`, `merge`, `link`. [Read more](./project/toc.md#include-mode).

* If the toc includes another one under the `root_merge` and `merge` modes, the original path will be added
  to the `sourcePath` meta field.
*
### yfm-transform

#### 2.4.0

* [Multiline tables](./syntax/tables/multiline.md) enabled by default.

#### 2.3.0

* Added support [monospaced text](./syntax/base.md).

## November 2021

### yfm-docs

#### 1.15.0

* Added the ability to include `toc.yaml` with the addition of its elements to the same table of contents level.

  [Read more](./project/toc.md#include-as-pages)

#### 1.14.0

* Added the ability to [configure the linter](./project/lint.md)

### yfm-transform

#### 2.2.0

* Added the ability to redefine delimiters in the plugin [markdown-it-attrs](https://www.npmjs.com/package/markdown-it-attrs).

## October 2021

### yfm-transform

#### 2.1.0

* Added beta-plugin for support multiline tables.

## September 2021

### yfm-docs

#### 1.13.0

* YFM2 is used

### yfm-transform

#### 2.0

* YFM can be used on the client.
* The plug-in connection scheme has been changed.
* The [markdown-it-attrs](https://www.npmjs.com/package/markdown-it-attrs) plugin is always connected.
* The [highlight.js](https://www.npmjs.com/package/highlight.js) package must be installed independently.

## July 2021

### yfm-docs

#### 1.12.0

* The experimental YFM linter was disabled.

### yfm-transform

#### 1.9.0

* Added the ability to enable support for GitHub compatible anchors (GFM).

## June 2021

### yfm-docs

#### 1.11.0

* An experimental YFM linter was enabled.

#### 1.10.0

* Now you can configure redirects using a special file. Static builds are not supported.

#### 1.9.0

* Added support for sections accessible only by direct link.

### yfm-transform

#### 1.8.0

* Added experimental linter support

## April 2021

### yfm-docs

#### 1.8.0

* Added the option to add file contributors to metadata. Only GitHub is supported out-of-the-box. It isn't displayed visually in any way, but can be used by a custom viewer.

## March 2021

### yfm-docs

#### 1.7.0

* Added complete disabling of variables: conditions are not calculated and values are not substituted.

### yfm-transform

#### 1.7.0

* Added complete disabling of variables: conditions are not calculated and values are not substituted.

## January 2021

### yfm-docs

#### 1.6.0

* Now you can build a document as a single HTML file.

#### 1.5.0

* Refactoring and bug fixes

#### 1.4.0

* Added disabling the calculation of conditions with variables.

### yfm-transform

#### 1.6.0

* Added support for loops, filters, and functions

#### 1.5.0

* Added a feature to use the `not_var` flag for variables that don't need to be substituted with values. For example, `not_var{{ variable_name }}`.

## October 2020

### yfm-docs

#### 1.3.0

* Added the ability to display built files on S3.

## August 2020

### yfm-docs

#### 1.2.0

* Now the documentation interface allows the user to change the font size, turn on the dark theme, and hide the table of contents.

### yfm-transform

#### 1.4.0

* Added an option to use '|' in variables.

## July 2020

### yfm-transform

#### 1.3.0

* Basic element styles have been updated.

#### 1.2.0

* Added support for inserting videos.

#### 1.1.0

* Added support for multiple custom anchors per header.

## June 2020

### yfm-docs

#### 1.1.0

* Added silent mode without outputting build logs.

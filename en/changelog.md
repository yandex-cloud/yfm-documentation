# Revision history

## December 2021

### yfm-docs

#### 1.17.0

* Don't remove not_var when output-format=md

#### 1.16.0

* Added modes for including toc: `root_merge`, `merge`, `link`. [Read more](./project/toc.md#include-mode)

* If the toc includes another one under the `root_merge` and `merge` modes, the original path will be added
to the `sourcePath` meta field


### yfm-docs

## November 2021

### yfm-docs

#### 1.15.0

* Added the ability to include `toc.yaml` with the addition of its elements to the same table of contents level.

  `toc.yaml`:
  
  ```yaml
  items:
    - name: Name1
      href: file1.md
      
    # Missing the name field of the element means that the elements 
    # of the included table of contents should be added to the same level 
    # of the table of contents, and not as a new section.
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
  The result is in the table of contents:
  - Name1
  - NameA
  - NameB
  - NameX

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


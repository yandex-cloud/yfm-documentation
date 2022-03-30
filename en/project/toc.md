# Table of contents

The document structure is described in a file named `toc.yaml`. This file defines how a table of contents is generated and documentation is built.

{% note warning %}

Files that are not specified in `toc.yaml` are not processed during the build.

{% endnote %}

## Structure {#structure}

The standard `toc.yaml` file structure looks like the following:

```yaml
title: Document name
href: index.yaml
items:
- name: Section name
  href: path/to/file.md
- name: Section group name
      items:
        - name: Section name
          href: path/to/file.md
        - name: Section name
          href: path/to/file.md
- name: Section name
  href: path/to/file.md
```

* `title`: Document name. It's displayed in the table of contents above the list of all sections.
* `name`: The name of a section or group of sections.
* `href`: The relative path to the file.
* `items`: A grouping element.

## Section visibility conditions {#when}

Individual sections can be included in or excluded from the document, depending on the values of [variables](../syntax/vars.md). To describe visibility conditions, the `when` parameter is used.

Possible comparison operators: `==`, `!=`, `<`, `>`, `<=`, and `>=`.

```yaml
- name: Section with conditional inclusion
  href: path/to/conditional/file.md
  when: version == 12
```

## Inserting tables of contents {#includes}

You can include the table of contents of another document (a different `toc.yaml` file) as a subsection in your document. To do this, use the parameters:

* `include`: An element that allows you to include a different table of contents. Must contain the `path` child element.
* `path`: The path to the table of contents to be included.

Inserting tables of contents allows you to independently maintain separate sections and build a document from large blocks.

### Example with inclusion of the table of contents as a section {#include-as-section}

```yaml
- name: Name of an imported block
  include:
    path: another/toc.yaml
```

### Example with inclusion of a table of contents without creating a section {#include-as-pages}

There is also the ability to include `toc.yaml` with the addition of its elements to the same table of contents level.

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

### mode {#include-mode}

`include` may contain the `mode` child element.
`mode` - the mode of inclusion of the table of contents.

Possible values: `root_merge`, `merge`, `link`. Default value: `root_merge`.

Differences:
- `merge` and `link` - `path` is relative to the table of contents in which the inclusion occurs.
- `root_merge` - `path` is relative to the root of the documentation.
- `root_merge` and `merge` - all files and directories located next to the included table of contents 
are moved to the directory of the table of contents in which the inclusion occurs. Moving occurs with overwriting of files.
Since the project structure changes during moving, a `sourcePath` with the path to the source file is added to the metadata of the files.
This field is used for a link to edit the page.
- `link` - the project structure does not change. All links of the included table of contents are changed to links relative 
to the table of contents in which the inclusion occurs.

## Hidden sections {#hidden}

To make a section accessible only by a direct link and excluded it from the table of contents, specify the `hidden` parameter.

```yaml
- title: Secret document
  href: secret.md
  hidden: true
```

To completely exclude hidden sections from the build, use the [build key](../tools/docs/settings.md) `--remove-hidden-toc-items=true`.


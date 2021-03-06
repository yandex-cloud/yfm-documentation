# Links

The standard markup for a link is:

```
[link_text](link "hint_text")
```

  * `link_text`: The link text.
  * `link`: A URL or path to a file.
  * `"hint_text"`: A hint that will be displayed when you hover over the link text. Optional.

Depending on the type of link, simplifications and other design options are allowed.

## Link to MD file {#autotitle}

You can create a link to an MD file without explicitly specifying the link text. To do this, add the symbols `{#T}` in place of the text, and they will automatically be substituted with the title of the specified file.

```markdown
[{#T}](./index.md)
```

**Result**

[{#T}](./index.md)

## A URL or an email address {#url-email}

To convert a URL or an email address to a link, add angle brackets `<>` on both sides.

```markdown
<https://yandex.com/>

<alice.the.girl@yandex.com>
```

**Result**

<https://yandex.com/>

<alice.the.girl@yandex.com>

## Reference-style markup for links {#reference-style}

Use reference-style links to make the source text of a document easier to read. These links consist of two parts connected by tags:

* A brief link description in the text.

  `[link_text][link_tag]`

* A long URL placed in a special place at the end of a paragraph or document.

  `[link_tag]: URL`

```markdown
My favorite search engine is [Yandex][1].

[1]: https://yandex.com/ "The best search engine"
```

**Result**

My favorite search engine is [Yandex][1].

[1]: https://yandex.com/ "The best search engine"
## Link text style {#formatting}

You can apply [line formatting](./base.md#line) to the link text.

```markdown
I love the **[Yandex Cloud](https://cloud.yandex.com)**.
This is the _[YFM Guide](https://yadocs.tech)_.
See the section on [`code`](#code).
Super [^men^](https://en.wikipedia.org/wiki/Major_Grom_(2017_film)).
```

**Result**

I love **[Yandex.Cloud](https://cloud.yandex.com)**.
This is the _[YFM Guide](https://yadocs.tech)_.
See the section on [`code`](#code).
Super [^men^](https://en.wikipedia.org/wiki/Major_Grom_(2017_film)).


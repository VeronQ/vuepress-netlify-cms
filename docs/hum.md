---
title: Hum..
---
# Markdown Extensions

## Header Anchors

Headers automatically get anchor links applied. Rendering of anchors can be configured using the [`markdown.anchor`](#) option.

## Links

### Internal Links

Inbound links ending in `.md` or `.html` are converted to `<router-link>` for SPA navigation.

Each sub-directory in your static site should contain a `README.md`. It will automatically be converted to `index.html`.

::: tip TIP
When writing the relative path to a directory's index.html, don't forget to close it off with a /, otherwise you will get a 404. For example, use /config/ instead of /config.
:::

If you want to link to another markdown file within a directory, remember to:

1. Append it with either `.html` or `.md`
2. Make sure the case matches since the path is case-sensitive

#### Example

Given the following directory structure:

```
.
├─ README.md
├─ foo
│  ├─ README.md
│  ├─ one.md
│  └─ two.md
└─ bar
   ├─ README.md
   ├─ three.md
   └─ four.md
```

``` md
[Home](/) <!-- Sends the user to the root README.md -->
[foo](/foo/) <!-- Sends the user to index.html of directory foo -->
[foo heading anchor](/foo/#heading) <!-- Anchors user to a heading in the foo README file -->
[foo - one](/foo/one.html) <!-- You can append .html -->
[foo - two](/foo/two.md) <!-- Or you can append .md -->
```

### External Links

Outbound links automatically gets `target="_blank" rel="noopener noreferrer"`:

* [vuejs.org](#)
* [VuePress on GitHub](#)

You can customize the attributes added to external links by setting [config.markdown.externalLinks](#).

## Front Matter

[YAML front matter](https://example.com) is supported out of the box:

``` yaml
title: Blogging Like a Hacker
lang: en-US
```

The data will be available to the rest of the page, plus all custom and theming components.

For detailed introduction, please move to [Front Matter](#).

## GitHub-Style Tables

**Input**

```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```

**Output**

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

## Emoji :tada:

**Input**

```
:tada: :100:
```

**Output**

:tada: :100:

A list of all emojis available can be found [here](https://example.com).

## Table of Contents

**Input**

```
[[toc]]
```

**Output**

[[toc]]

Rendering of TOC can be configured using the [`markdown.toc`](#) option.

## Custom Containers

**Input**

```
::: tip
This is a tip
:::

::: warning
This is a warning
:::

::: danger
This is a dangerous warning
:::
```

**Output**

::: tip
This is a tip
:::

::: warning
This is a warning
:::

::: danger
This is a dangerous warning
:::

You can also customize the title of the block:

```
::: danger STOP
Danger zone, do not proceed
:::
```

::: danger STOP
Danger zone, do not proceed
:::

## Line Highlighting in Code Blocks

**Input**

```
``` js{4}
export default {
  data () {
    return {
      msg: 'Highlighted!'
    }
  }
}
```


**Output**

``` js{4}
export default {
  data () {
    return {
      msg: 'Highlighted!'
    }
  }
}
```

## Line Numbers

You can enable line numbers for each code blocks via config:

``` js
module.exports = {
  markdown: {
    lineNumbers: true
  }
}
```

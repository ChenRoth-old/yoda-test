---
layout: bt_wiki
title: Cheat Sheet
category: internal
draft: true
weight:  700
parent:  none
---

# Text Formatting

hugo
| **Description** | **Syntax** | **Output** |
|-------------|----------------|-------------
| Emphasized text | \*emphasized\*. | *emphasized*. |
| Bold text | \*\*bold\*\*. | **bold**. |
| Inline code | \`\`\`print "hello world!"\`\`\` | ```print "hello world!"``` |
hugo

## Tags

You can add decorative tags:

**Syntax**:

```md
hugo
```

**Output**:

hugo

# Code Blocks

To add code blocks of a specific language, e.g. python, type this:

~~~md
```python

# this is python code

def hello_world():

  print "Hello World!"

```
~~~

Output:

```python
# this is python code

def hello_world():
  print "Hello World!"
```

# Links

hugo
| **Description** | **Syntax** | **Output** |
|-----------------|--------------|------------|
| Link to external site | ```[GigaSpaces](http://www.gigaspaces.com)``` | [GigaSpaces](http://www.gigaspaces.com) |
| Link to a page in docs | ```[Cloudify REST Client](hugo) |
| Link to an anchor in page | ```[Text Formatting\](#text-formatting)```, where 'text-formatting' is the anchored DOM element id | [Text Formatting](#text-formatting) |
hugo

## Link to latest
To create a link that will always point to the latest version of the docs, use `/latest/`:
```md
[I'm a link](/latest/intro/what-is-cloudify)
```
Will redirect to `http://docs.getcloudify.org/\<LATEST_VERSION_NUMBER\>/intro/what-is-cloudify

# Tables

**Syntax**:

```md
hugo
| heading 1 | heading 2 |
|-----------|-----------|
| cell 1x1  | cell 1x2  |
| cell 2x1  | cell 2x2  |
hugo
```

**Output**:

hugo
| heading 1 | heading 2 |
|-----------|-----------|
| cell 1x1  | cell 1x2  |
| cell 2x1  | cell 2x2  |
hugo


# Images

To add an image, copy it to a path of your choice within ```/static/images/```

You can then refer to the image path, relative to ```/static/images/```:

hugo
| **Syntax** | **Output** |
|------------|------------|
| ```![Jon Lovitz](hugo) |
hugo

# Panels

## Tip

**Syntax**:

``` hugoIf you're drunk, go homehugo ```

**Output**:

hugo

## Info

**Syntax**:

``` hugoUnicorns are realhugo ```

**Output**:

hugo

## Note

**Syntax**:

``` hugoPlease remember to flushhugo ```

**Output**:

hugo

## Warning

**Syntax**:

``` hugoThe gorilla bites!hugo ```

**Output**:

hugo

# Page Fields

You can add custom fields to the page metadata and use these fields within the page.

**Syntax**:

In page metadata (Front Matter):
```yaml
---
title: my page

favorite_food: icecream
---
```

In page content:
```md
I love hugo!
```

**Output**:
```
I love icecream!
```


# Hands-on markdown tutorial

> mostly (adapted) from <https://daringfireball.net/projects/markdown/dingus> and

## Software

Try writing a markdown document, using either

1. an online markdown editor (e.g. <https://demo.hedgedoc.org/new>),
1. the GitHub or GitLab IDE to create / adapt the `README.md`, or
1. (advanced) your favorite text-editor that supports markdown.

## Basic Syntax

### Phrase Emphasis

*This is italic*   
_This is also italic_   
**This is bold**  
__This is also bold__ 

### Headers

# Header 1

## Header 2

###### Header 6

---- 

### Lists

#### Ordered, without paragraphs:

1. Item 1 
2. Item 2
4. Item 3


> Note the "4." in md

#### Unordered, with paragraphs:

- A list item.
- Bar
You can nest them:
- Abacus
  * answer
  * Bubbles
    1. bunk
    2. bupkis
      - BELITTLER
    3. burper

> Note: indentation matters

### Blockquotes

> Email-style angle brackets
> are used for blockquotes.

> > And, they can be nested.

> #### Headers in blockquotes
>
> - You can quote a list.
> - Etc.

### Code Spans

- `<code>` spans are delimited by backticks.

- You can include literal backticks like `` `this` ``.

### Code Blocks

```
This is a code block
```

### Horizontal Rules

Three or more dashes or asterisks:

---

* * *

- - - -

### Manual Line Breaks

End a line with two or more spaces:
Roses are red,  
Violets are blue.

### Links

- Inline:
  An [example](http://url.com/ "Title")

- Reference-style labels (titles are optional):
  An [example][id]. Then, anywhere else in the doc, define the link:

  [id]: http://example.com/  "Title"

### Images

- Inline (titles are optional):
![alt text](/path/img.jpg "Title")

- Reference-style:
![alt text][id]

[id]: /url/to/img.jpg "Title"

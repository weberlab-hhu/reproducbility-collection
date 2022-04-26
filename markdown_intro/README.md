
# TODOS

# Intro to Markdown

- [What is Markdown?](#what-is-markdown)
- [Why Markdown?](#why-markdown)
- [Is there anything markdown can't do?](#is-there-anything-markdown-cant-do)
- [Markdown <> Code & Data Management?](#markdown--code--data-management)
- [Good to know](#good-to-know)
  - [Implementations and variants](#implementations-and-variants)
  - [Converting markdown files](#converting-markdown-files)
  - [Real-time collaboration](#real-time-collaboration)
  - [Tutorials and resources](#tutorials-and-resources)
- [Markdown and VS Code](#markdown-and-vs-code)
  - [Recommended VS code extensions](#recommended-vs-code-extensions)
  - [Things that are very easy with extensions](#things-that-are-very-easy-with-extensions)

## What is Markdown?

- Markdown is a lightweight markup language
  - Other markup languages: HyperText Markup Language (HTML), Extensible Markup Language (XML), LaTeX
- WYSIWYG: "What You See Is What You Get"
- Official website: <https://daringfireball.net/projects/markdown/>

----

**In HTML:**

```html
<html>
  <body>    
    <h3>headline level 3</h3>
    <h4>headline level 4</h4>
    <h3>headline level 5</h5>
  </body>
</html>
```

**In Markdown:**

```
  ### headline level 3
  #### headline level 4
  ##### headline level 5
```

**Rendered output:**

### headline level 3 <!-- omit in toc -->

#### headline level 4 <!-- omit in toc -->

##### headline level 5 <!-- omit in toc -->

----

**In HTML:**

```html  
  <ul>
    <li>List item 1</li>
    <li><strong>List item 2 in bold</strong></li>
  </ul>
```

**In Markdown:**

```
  - List item 1
  - **List item 2 in bold**
```

**Rendered output:**

- List item 1
- **List item 2 in bold**

## Why Markdown?

- simple, plain text format
  - no hassle with formatting
  - Worry about content, not layout.
  - Most benefits of [LaTeX], but simpler
- easy-to-read, easy-to-write
  - intuitively human-readable
  - machine-actionable, convertible
- independent
  - open source
  - You only need a text editor
  - No need for "word processor programs"
    - Microsoft Word, WordPad, macOS Pages, Google Docs, LibreOffice Writer
- reusable
  - text is not stuck in formats or layouts
- extendible
  - many programs and tools work with markdown

## Is there anything markdown can't do?

- Beautiful, perfectly designed documents or slide shows
  - Reminder: "WYSIWYG"
  - Theming, customization, special formatting, design is hard(ly possible)
  - Use a word processor (or [LaTeX] ;)
- Collaboration on documents (e.g. reviewing)
  - comments, suggestions, discuss changes, text highlighting

## Markdown <> Code & Data Management?

- Works perfectly with (text based) version-control
  - Changes can easily be tracked via git
  - Many GitHub / GitLab features are based on MD
    - README.md, issues, wiki pages, discussions and comments
  - referencing files and folders, e.g. in a README.md
- Integrated development environments (IDEs)
  - Jupyter Notebooks ~ markdown-commented python scripts
  - RMarkdown ~ markdown-commented R scripts

## Good to know

### Implementations and variants

- Markdown can be used in many programming languages, platforms and frameworks
  - RStudio (see [RMarkdown](https://rmarkdown.rstudio.com/))
  - GitHub (see [GitHub Flavored Markdown](https://github.github.com/gfm/), and )
  - Gitlab  
  - Microsoft Team Chats
  - Website generators (forget WordPress)

- **Note**: Different flavors to how and what is "interpreted"
  - e.g. not every markdown parser understands
    - emojis :bike:, :beers:, :tent:
    - <strong>bold html text</strong>
    - tables without headers

---------|----------|---------
 A1 | B1 | C1
 A2 | B2 | C2
 A3 | B3 | C3


----

### Converting markdown files

In case you want to provide your markdown document in another file format, converters help you.
The top recommendation: Pandoc![^1][Pandoc]
> Note: pandoc depends on a LaTeX Installation on your system.
> If you run into issues, see <https://pandoc.org/installing.html> for details and recommendations.

Use pandoc to convert your...

```bash
pandoc README.md -o README.html   # ... markdown to .html
pandoc README.md -o README.pdf    # ... markdown to .pdf
pandoc README.md -o README.docx   # ... markdown to .docx
pandoc -t slidy -s --slide-level=2 --metadata pagetitle=markdown_intro README.md -o markdown_slides.html # ... markdown to html slides
pandoc -t s5 -s --slide-level=2 --metadata pagetitle=markdown_intro README.md -o markdown_slides.html # ... markdown to html slides
```

### Real-time collaboration

- <https://hedgedoc.org>
- <https://github.com/hackmdio/codimd>
  - HHU Members: <https://pad.hhu.de>

### Tutorials and resources

- Markdown Guide: <https://www.markdownguide.org/>
- Commonmark Tutorial: <https://commonmark.org/help/tutorial/>
- Cheat sheets:
  - <https://www.markdownguide.org/cheat-sheet/>
  - <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>
  - <https://daringfireball.net/projects/markdown/dingus>
- Markdown emojis <https://gist.github.com/rxaviers/7360908>

## Markdown and VS Code

### Recommended VS code extensions

1. [Microsoft Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack), including
    - [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
    - [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
1. [Markdown Shortcuts](https://marketplace.visualstudio.com/items?itemName=mdickin.markdown-shortcuts)
1. [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf)
1. [Markdown all in one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)

### Things that are very easy with extensions

- Creating a table
- Copy/pasting a table from excel
- Converting a markdown to PDF
- "Formatting"
- Creating a TOC

<!-- This is just to show references in markdown -->

[LaTeX]: https://www.latex-project.org/

<!-- This is just to show you a footnote in markdown -->

[^1]: <https://pandoc.org/>

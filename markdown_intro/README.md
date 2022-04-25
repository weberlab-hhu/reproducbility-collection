
# Intro to Markdown

- [What is Markdown?](#what-is-markdown)
- [Why Markdown?](#why-markdown)
  - [Is there anything markdown can't do?](#is-there-anything-markdown-cant-do)
  - [Markdown &harr; Code & Data Management?](#markdown--code--data-management)
- [Good to know](#good-to-know)
  - [interpreters, parsers](#interpreters-parsers)
  - [Converting markdown files](#converting-markdown-files)
- [Tutorials and resources](#tutorials-and-resources)
- [Markdown and VS Code](#markdown-and-vs-code)
  - [Keyboard Shortcuts (mac)](#keyboard-shortcuts-mac)
  - [Recommended VS code extensions](#recommended-vs-code-extensions)
  - [Things that are very easy with extensions](#things-that-are-very-easy-with-extensions)

## What is Markdown?

- a markup language
- compare HTML (hyper text markup language)
- WYSIWYG: "What You See Is What You Get"
- https://daringfireball.net/projects/markdown/

In HTML

```html
  <ul>
  <li>List item 1</li>
  <li>List item 2</li>
  </ul>
```

In Markdown:

```markdown
  - List item 1
  - List item 2 
```

Rendered output:

- List item 1
- List item 2

https://daringfireball.net/projects/markdown/dingus

## Why Markdown?

- simple, plain text format
  - no hassle with formatting
- easy-to-read, easy-to-write
  - intuitively human-readable
  - machine-actionable, convertible  
- independent
  - open source
  - you need nothing but a simple text editor  
- reusable
  - text is not stuck in formats
- extendible
  - many programs and tools work with markdown

- Almost like [LaTeX], but simpler.

### Is there anything markdown can't do?

- Customization, special formatting, design. (-> WYSIWYG)
- Collaboration (think cloud docs)
  - commenting

### Markdown &harr; Code & Data Management?

- Works perfectly with (text based) version-control
  - Changes can easily be tracked via git
  - Many GitHub / GitLab features are based on MD
    - README.md, issues, wiki pages, discussions and comments
  - referencing files and folders, e.g. in a README.md
- Integrated development environments (IDEs)
  - Jupyter Notebooks ≈ markdown-commented python scripts
  - RStudio RMarkdown ≈ markdown-commented R scripts

## Good to know

### interpreters, parsers

- Different flavors to how and what is "interpreted"
  - e.g. not every markdown parser understands emojis :check:

GitHub Flavored Markdown https://github.github.com/gfm/
RMarkdown https://rmarkdown.rstudio.com/

### Converting markdown files

In case you want to provide your markdown document in another file format, converters help you.
The top recommendation: Pandoc! <https://pandoc.org/>
> Note: pandoc depends on LaTeX on your system.\
> If you run into issues, see <https://pandoc.org/installing.html> for details and recommendations.

Use pandoc to convert your... 

```bash
pandoc README.md -o README.html   # ... markdown to .html
pandoc README.md -o README.pdf    # ... markdown to .pdf
pandoc README.md -o README.docx   # ... markdown to .docx
```

## Tutorials and resources

- Markdown Guide: <https://www.markdownguide.org/>
- Commonmark Tutorial: https://commonmark.org/help/tutorial/
- Cheat sheets:
  - <https://www.markdownguide.org/cheat-sheet/>
  - https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

## Markdown and VS Code

### Keyboard Shortcuts (mac)

- Preview: 1. [CMD-K], 2. [V]
- Duplicate: [CMD]+[Shift]+[D]
- Command Palette: [CMD]+[Shift]+[P]

### Recommended VS code extensions

1. [Microsoft Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack), including
    - [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)
    - [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)

2. [Markdown Shortcuts](https://marketplace.visualstudio.com/items?itemName=mdickin.markdown-shortcuts)

3. [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf)

4. [Markdown all in one](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)

### Things that are very easy with extensions

- Creating a table
- Copy/pasting a table from excel
- Converting to a markdown PDF
- "Formatting"
- Creating a TOC



<!-- This is just to show references in markdown -->

[LaTeX]: https://www.latex-project.org/
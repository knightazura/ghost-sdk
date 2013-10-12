[work in progress]...obviously

Haunted Markdown is based on John Gruber's original Markdown project, and borrows from Github Flavored Markdown and MultiMarkdown. It has a focus on producing consistent results whilst editing, so that the experience of live previewing is smooth.

### Features

Haunted Markdown should support the following features:
* Markdown paragraphs and line breaks
* Setext & atx style headings
* GFM style line breaking
* Block quote with `>`
* Horizontal rules with `* * *`, `***`, `*****`, `- - -`, `----------------------`
* Emphasis & strong with `*`, `**`, `_`, `__`, characters but which allows spaces before the closing markdown character so that the style of the output doesn't change whilst typing.
* Strike through with `~~`
* Reference and inline links, with titles `[alt](http://ghost.org "optional title")` or `[ref]: http://ghost.org  "optional title"`
* Reference and inline images, with titles/captions
* Reference and inline video, with titles/captions (we don't know what this is gonna look like yet)
* Both Markdown and GFM style autolinking

### Specification
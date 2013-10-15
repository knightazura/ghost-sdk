[work in progress]...obviously

Haunted Markdown is based on John Gruber's original Markdown project, and borrows from Github Flavored Markdown and MultiMarkdown. It has a focus on producing consistent results whilst editing, so that the experience of live previewing is smooth.

### Areas of Research

This section covers available implementations and current efforts to create a Markdown specification. Since the original Markdown Syntax proposed by John Gruber can be considered abandonware, the community started implementing various dialects of Markdown in order to fix flaws and provide additional features. 

There is a [Markdown Group](http://www.w3.org/community/markdown/) at W3, inspired by a post from [Jeff Atwood](http://www.codinghorror.com/blog/2012/10/the-future-of-markdown.html), that was created in 2012 in order to create a specification for Markdown. The group seems dead as of December 2012 (last post in Wiki).

Another community initiated project tries to collect [all available Markdown implementations](https://github.com/markdown/markdown.github.com/wiki/Implementations) but has also not received any update since March 2013 and can be considered abandoned.

The available NodeJS based Markdown implementations can be categorized into two groups: RegEx Converters ([showdown](https://github.com/coreyti/showdown), [marked](https://github.com/chjj/marked), [markdown-js](https://github.com/evilstreak/markdown-js)) and Wrappers ([node-multimarkdown](https://github.com/dtjm/node-multimarkdown), [node-markdown](https://github.com/andris9/node-markdown), [RoboSkirt](https://github.com/benmills/robotskirt), [node-discount](https://github.com/visionmedia/node-discount)). Wrappers would add new system dependent dependencies and RegEx based converters are hard to extend and not context aware.

John MacFarlane created a [great tool](http://johnmacfarlane.net/babelmark2/) to compare the output of multiple available Markdown implementations, which will become helpful in validating output of whatever library is chosen or built for HauntedMarkdown.

### Features

Haunted Markdown should support the following features:

* Markdown escaping of `&` and `<`
* Markdown paragraphs and line breaks
* Setext & atx style headings i.e. headings prefixed with `#` or underlined with `_` or `=`
* GFM style line breaking
* Blockquote with `>`, indented blockquotes 
* Horizontal rules with `* * *`, `***`, `*****`, `- - -`, `----------------------`
* Emphasis with `*` & `_`, and strong with `**` & `__` but which allows spaces at the end of the string between the markdown characters so that the style of the output doesn't change whilst typing.
* GFM style handling of underscores inside words
* Strike through with `~~`
* Bulleted lists with `*` or `-`, numbered lists
* Advanced list indenting (needs much consideration)
* Reference and inline links, with titles `[alt](http://ghost.org "optional title")` or `[ref]: http://ghost.org  "optional title"`
* Reference and inline images, with titles/captions
* Reference and inline video, with titles/captions (we don't know what this is gonna look like yet)
* Both Markdown and GFM style autolinking
* Indented, fenced and inline code blocks
* Full HTML support

### Specification
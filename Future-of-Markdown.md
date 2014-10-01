Markdown is the heart of Ghost, and as such we intend to make working with it one of our core competencies.

The version of Markdown used in Ghost is based on John Gruber's original [Markdown project](http://daringfireball.net/projects/markdown/), and borrows from [Github Flavored Markdown](https://help.github.com/articles/github-flavored-markdown) and [MultiMarkdown](http://fletcherpenney.net/multimarkdown/). It has a focus on producing consistent results whilst editing, so that the experience of live previewing is smooth.

We intend to create excellent tools for working with Markdown in Ghost, and surpass the existing solution which uses CodeMirror and Showdown.


### Parsing Markdown

Parsing markdown is no simple task. Here's some interesting stuff I've collected about parsing markdown

http://stackoverflow.com/questions/605434/how-would-you-go-about-parsing-markdown

http://www.cforcoding.com/2010/02/markdown-block-parsing-and-road-to-hell.html

http://blog.stackoverflow.com/2008/06/three-markdown-gotcha/


### Current Implementations

This section covers available implementations and current efforts to create a Markdown specification. Since the original Markdown Syntax proposed by John Gruber can be considered abandonware, the community started implementing various dialects of Markdown in order to fix flaws and provide additional features. 

There is a [Markdown Group](http://www.w3.org/community/markdown/) at W3C, inspired by a post from [Jeff Atwood](http://www.codinghorror.com/blog/2012/10/the-future-of-markdown.html), that was created in 2012 in order to create a specification for Markdown. The group seems dead as of December 2012 (last post in Wiki), as discussed on its mailing list in October 2013 [where Haunted Markdown is mentioned](http://lists.w3.org/Archives/Public/public-markdown/2013Oct/0004.html).

Another community initiated project tries to collect [all available Markdown implementations](https://github.com/markdown/markdown.github.com/wiki/Implementations) but has also not received any update since March 2013 and can be considered abandoned.

There is a fairly active [`markdown-discuss` mailing list](http://six.pairlist.net/pipermail/markdown-discuss/).

The available NodeJS based Markdown implementations can be categorized into two groups: RegEx Converters ([showdown](https://github.com/coreyti/showdown), [marked](https://github.com/chjj/marked), [markdown-js](https://github.com/evilstreak/markdown-js)) and Wrappers ([node-multimarkdown](https://github.com/dtjm/node-multimarkdown), [node-markdown](https://github.com/andris9/node-markdown), [RoboSkirt](https://github.com/benmills/robotskirt), [node-discount](https://github.com/visionmedia/node-discount)). Wrappers would add new system dependent dependencies and RegEx based converters are hard to extend and not context aware.

John MacFarlane created a [great tool](http://johnmacfarlane.net/babelmark2/) to compare the output of multiple available Markdown implementations, which will become helpful in validating output of whatever library is chosen or built for HauntedMarkdown.

### Features

Ghost's Markdown is based on John Gruber's original Markdown project, and borrows from Github Flavored Markdown and MultiMarkdown. It has a focus on producing consistent results whilst editing, so that the experience of live previewing is smooth.

Ghost wants to support the following features:

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
* Reference and inline images, with titles/captions. Currently we only support image uploads where the image is on a new line on it's own. It would be nice to look at ways to improve that.
* Reference and inline video, with titles/captions (we don't know what this is gonna look like yet)
* Both Markdown and GFM style autolinking
* Indented, fenced and inline code blocks
* Full [HTML support](HTML support)
* MultiMarkdown features? TBC

### Specification

The goal is to create something like: https://github.com/mustache/spec
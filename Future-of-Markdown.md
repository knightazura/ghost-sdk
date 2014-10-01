Markdown is the heart of Ghost, and as such we intend to make working with it one of our core competencies.

The version of Markdown used in Ghost is dubbed 'Haunted Markdown'. Haunted Markdown is based on John Gruber's original [Markdown project](http://daringfireball.net/projects/markdown/), and borrows from [Github Flavored Markdown](https://help.github.com/articles/github-flavored-markdown) and [MultiMarkdown](http://fletcherpenney.net/multimarkdown/). It has a focus on producing consistent results whilst editing, so that the experience of live previewing is smooth.

We intend to create excellent tools for working with Haunted Markdown, and surpass the existing solution which uses CodeMirror and Showdown.

The long term plan for Markdown in Ghost looks something like:

1. Complete the initial draft of the specification for [Haunted Markdown](https://github.com/TryGhost/Ghost/wiki/Haunted-Markdown)
2. Develop a standalone parser module for Haunted Markdown, which converts the Markdown into tokens (and doesn't use regular expressions to do it)
3. Extend the parser to be able to convert tokens to HTML, and wire this up in Ghost as the tool we use to convert Markdown to HTML
4. Use the parser to create a mode for CodeMirror which converts the tokens into styles

At this point, we should achieve a consistent experience in the editor in terms of the mapping from Markdown to HTML. For example, we should no longer get hex strings styled differently in CodeMirror but ignored by the preview, or see situations where things are italic on one screen but not the other.

In the even more distant future, with our Markdown parser in hand, we want to replace CodeMirror altogether with a purpose built editor capable of handling Haunted Markdown, and which provides the hooks we need to create a better relationship between the editor and preview.


### Parsing Markdown

Parsing markdown is no simple task. Here's some interesting stuff I've collected about parsing markdown

http://stackoverflow.com/questions/605434/how-would-you-go-about-parsing-markdown

http://www.cforcoding.com/2010/02/markdown-block-parsing-and-road-to-hell.html

http://blog.stackoverflow.com/2008/06/three-markdown-gotcha/
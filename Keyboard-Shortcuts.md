The following document outlines the keyboard shortcuts in place in the backbone Ghost admin, and the keyboard shortcuts as we want them to exist in the shiny new Ember admin. At the end is a big list of research I did for various shortcuts along with a rough explanation of what they all do.

There are a few important things to consider. 
 * Some of these keyboard shortcuts relate to quite advanced pieces of functionality which are only accessible via a keyboard shortcut (e.g zen mode). It may be the case that the functionality doesn't work yet in the Ember admin, but it will need to so we may need to make new issues.
 * The markdown shortcuts have some very specific expected behaviour, in particular around where the cursor starts and where the cursor ends - for example if you press `Ctrl+B` without any text selected, you should get 4 `*`'s with the cursor in the middle (i.e. `**|**`) and I believe if you select text and do it, the selected text should be wrapped in bold and the cursor should appear after. Much of this seems to be broken.
 * Long after we implemented the editor we realised that CodeMirror has some quite odd shortcuts of it's own: https://github.com/marijnh/CodeMirror/blob/master/lib/codemirror.js#L4675 and at least some of them (like Ctrl+D) need to be disabled - this needs auditing / reviewing.

## Ember (new)

### Other/General shortcuts
* `ESC` - Close notification
* `ESC` - Close modal

### Content screen

* `UP` - navigate up through post list
* `DOWN` - navigate down through post list

### Editor Markdown shortcuts
**Note** Where there is a `⌘`, the shortcuts should be split and the `⌘` version registered if the current device is mac, and the non-`⌘` version registered otherwise. `if (navigator.userAgent.indexOf('Mac') !== -1)` is sufficient to determine which to use.

* `Ctrl/⌘ + B` - **Bold Text** 
* `Ctrl/⌘ + I` - *Italic Text*
* `Ctrl/⌘ + Alt + C` - Copy HTML
* `Ctrl/⌘ + K` - Link
* `Ctrl + Shift+  I` - image - not sure if we should change this one at all? It might be good to have `⌘ + Shift + 1` on mac?


### Editor General shortcuts 
* `Alt + Shift + Z` - Zen writing mode

##### Save button 
* `Ctrl/⌘ + S` - Save / Update post


## Backbone (existing)

### Editor general shortcuts
##### Top level
* `Ctrl+Alt+C` - HTML copy & paste
* `Alt+Shift+Z` - Zen writing mode
##### Save button 
* `Ctrl+S` - Save / Update post
* `Meta+S` - Save / Update post
* `Ctrl+Alt+P` - Publish post

### Editor Markdown shortcuts
##### All
* `Ctrl+Alt+U` - strike
* `Ctrl+Shift+K` - code
* `Meta+K` - code
* `Ctrl+Alt+1` - h1
* `Ctrl+Alt+2` - h2
* `Ctrl+Alt+3` - h3
* `Ctrl+Alt+4` - h4
* `Ctrl+Alt+5` - h5
* `Ctrl+Alt+6` - h6
* `Ctrl+Shift+L` - link
* `Ctrl+Shift+I` - image
* `Ctrl+Q` - blockquote
* `Ctrl+Shift+1` - currentDate
* `Ctrl+U` - uppercase
* `Ctrl+Shift+U` - lowercase
* `Ctrl+Alt+Shift+U` - titlecase
* `Ctrl+Alt+W` - selectword
* `Ctrl+L` - list

##### Mac only:
* `Meta+B` - bold
* `Meta+I` - italic
* `Meta+Alt+C` - copyHTML
* `Meta+Enter` - newLine

##### Non Mac:
*`Ctrl+B` - bold
*`Ctrl+I` - italic
*`Ctrl+Alt+C` - copyHTML
*`Ctrl+Enter` - newLine

### Other shortcuts
* `ESC` - Close notification
* `ESC` - Close modal


## Research & Details for each action

Sources:
* Google docs [shortcuts](https://support.google.com/docs/answer/179738?hl=en)
* Gmail [formatting](https://support.google.com/mail/answer/8260?authuser=2) [general shortcuts](https://support.google.com/mail/answer/6594?authuser=2)
* Mou App (see actions) http://mouapp.com/
* Common keyboard shortcuts [wikipedia](http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts)

### Shortcuts that are obvious / decided on:

**Bold Text**  
`Ctrl/⌘ + B` - this is ubiquitous

*Italic Text*  
`Ctrl/⌘ + I` - this is ubiquitous

[Link](http://example.com)

`Ctrl/⌘ + K` - from office, gmail and google docs

### Shortcuts that need research / decisions:

~~Strikethrough~~

* Old Ghost - `Ctrl + Alt + U`
* Google docs - `Alt + Shift + 5`
* Mou App - `⌘ + U` - as though it was underline, markdown has no underline, so Ctrl/⌘ + U might be good?

**Image**

**List**

**Code** - Inline code

**Code Block** - block of code (only inline had a shortcut before)

**Blockquote**

**CurrentDate**

**Uppercase**

**Lowercase**

**Titlecase**

**Select Word**

**Horizontal Rule** - not present in old admin

**Copy HTML** - a.k.a copy with styling
These documents formed the original basis around which Ghost was developed and are here for historical purposes only:

# User Stories

A set of user stories describing common interactions in Ghost

###Admin Screen: 

* [Write Post](#write-post)
* [Manage Posts](#manage-posts)
* [Manage Posts (Mobile)](#manage-posts-%28mobile%29)
* [Settings Management](#settings-management)

---

## Write Post

Our user is called Bob. 

##Writing The Content

* Bob writes a title in the title box area
* Bob writes his content in the content box using markdown
* On the right, another panel updates on the fly with a live, rendered preview

##Adding an Image

* When Bob comes to a place in his text where he wants to add an image, he hits enter a couple of times. Images cannot be floated within text. They always appear as a new paragraph.
* In this instance, Bob knows the url of the image he wants to embed. He's got it on his clipboard already. He writes `!image[alt text](http://path/to/img.jpg)` and the image appears in the preview pane.
* A little later, Bob reaches another place in the post where he wants to use an image. Of some Bananas. He's going to need to go and find an image, and he doesn't want stop writing, so he just types in the placeholder: `!image[Some Bananas]`
* The placeholder generates an upload form in the preview pane http://cl.ly/NxpQ
    * NB: The two icons in the corners should be added as non-functional placeholders only, for now. Later they will be "add image from URL" and "Take photo with camera" respectively.
* When Bob later uploads his image with this form, his Markdown syntax is automatically updated to `!image[Some Bananas](http://path/to/some-bananas.jpg)`

## Adding a Video

*This is a v0.5 function / vague implementation provided for reference only.*

* To add a video, Bob follows the same steps as when adding a video. The only difference is the syntax:
    * Full: `video[title](href)`
    * Placeholder: `video[title]`
    * The upload panel: http://cl.ly/Nvd3

## Adding a Tag - #2

* Once Bob has finished writing his post, he clicks on the "tag" icon in the bottom left hand corned of the screen
* The "tags" input field becomes enabled, and Bob starts typing the name of a tag in
* As Bob types, a live preview hints at existing tags which Bob can select - [like this](http://twitter.github.io/typeahead.js/)
* Bob can complete the tag entering process in any of the following ways:
    * Pressing enter
    * Pressing comma
    * Clicking on a tag in the autocomplete menu
    * Selecting a tag in the autocomplete menu with the up/down keyboard arrows, and pressing enter
* Each time Bob completes a tag, the tag is surrounded in a blue box - and Bob's cursor moves to the end of the row of tags, ready to type the next one.
* If Bob accidentally enters the wrong tag, he can simply click on it to remove it.

The design for this entire workflow: http://cl.ly/NvUD

## Changing Post Settings

The majority of the time, Bob would now move on to the "Publish" workflow. Sometimes, however, Bob might want to adjust a couple of settings about the post. To do this, he clicks on the cog icon in the bottom right hand corner of the screen.

http://cl.ly/NxEg

* Bob is now presented with a number of options to modify settings for this post. The first of which is "URL" allowing Bob to adjust the url for this specific post.
* Other settings, which can be added later, may include:
    * Make post featured
    * Change post author
    * Turn comments on/off (if comment partner is enabled)
    * Input SEO Title / Description (if enabled from SEO settings)
    * Custom settings added via a plugin hook
* When Bob has finished adjusting settings, he clicks anywhere on the screen to close the menu.
* All settings adjustments are saved automatically.

## Publishing

When Bob has completed his post, which is - it has to be said - a fucking masterpiece on Bananas and glue sniffing, he heads over to his final stop on this page: the publish button in the bottom right hand corner of the screen.

The publish button contains a number of functions which are selectable by Bob. The currently active function is printed as the button's label/value.

* When Bob clicks on the main area of the publish button, the button's action is invoked.
    * If the current action is "Publish Post" - a JavaScript alert is triggered to confirm the action
* When Bob clicks on the arrow on the button, the publish menu is opened - http://cl.ly/Nwmt
* The menu displays the available actions for this post, the currently active action is indicated with a tick.
* Clicking on an action replaces the button's current label/value with this action, and closes the menu.
* Clicking anywhere else on the screen closes the menu without updating anything.
    * Milestone Video Protoype requires: Save Draft, Publish to function. The rest can be dummy placeholders.
    * Milestone v0.1a requires: Save Draft, Publish, Schedule
* When Bob has selected and action, and then click on the button to invoke that action, the dropdown arrow is replaced by a loading spinner.
* He receives a visual notification as to the success (or failure) of his action.
    * Styling/Design TBC
* If the "Publish Post" action is invoked, following publication the Publish button changes to be an "Update" Button.
* Gracefully close post and return to post management screen(maybe?)(TBD)

(for now, let's ignore versioning completely)

----

## Manage Posts

To do that, Lucy uses the Content screen (Manage Posts) - http://cl.ly/NyOy

* When Lucy clicks on a post in the left hand column, the post is loaded into the right hand column. By default, the first post is selected.
* If Lucy clicks on the "All Posts" dropdown, she can choose which order to display posts in, or to search for a specific post. - http://cl.ly/NxkQ
* The post list has no other functions other than to select a post to preview.
* At the top of the post list, Lucy can click on the + button to start writing a new post. This will take her to the post editor (#5) with a blank post loaded.
* Once Lucy has selected a post to preview, she can perform a number of actions on it in the preview pane:
* Clicking on the *Star* icon in the header makes the post featured. Clicking on it again un-features the post.
* Clicking on the *Edit* icon in the header takes lucy to the post editor (#5) with this post loaded.
* Clicking on the *Settings* icon in the header loads the post settings menu (The same as the one in the bottom right-hand corner of the editor - #5) - http://cl.ly/Nyvd

Other notes:

* The preview pane can be styled via the theme
* The markup/output of the preview pane cannot be edited, only CSS.

----

## Manage Posts (Mobile)

This story is nearly identical to [Manage-Posts](#Manage-Posts), with a few exceptions:

Tablet:

* The post list is loaded - http://cl.ly/NzaL
* When the user clicks on a post, the entire content area flies off to the left (iOS style)
* Simultaneously to the above, the post preview flies in from the right - http://cl.ly/NzFp
* Clicking the back button takes the user back to the post-list

No other changed actions.

Mobile:

* Identical to tablet - some UI elements move slightly - http://cl.ly/NzXX

No changed actions

----

## Settings Management

###Settings (Desktop/Mobile/Everything)

User story for settings management. This is the main screen - http://cl.ly/O6v7

* User arrives on settings screen
* By default the first item in the list is selected
    * Use history API to remember the last sub-section the user was on and return to it?
* The settings relevant to the currently-active menu item are on the right
* The user can update the settings, and save them with the save button, top-right
    * Do we need a save button?
* Clicking on menu items on the left dynamically loads in the settings for other areas

Tablet workflow: Exactly the same, but smaller columns http://cl.ly/O6sC

Mobile workflow: Split into 2 pages, like other screens detailed http://cl.ly/O7TY
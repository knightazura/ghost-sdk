WIP

#Top Nav Bar

* G - highlights nicely on hover - is this supposed to have some function? Currently does nothing.
If there is currently no plan for this it would be nice if this took you to either the ghost website or a Ghost Foundation info page etc 

* Dashboard - takes to dashboard tab - working

* Content - takes to content tab - working

* New Post - takes to editor tab - working

* Settings -  takes to settings tab - working


### User drop-down menu

Who is the ugly git in the picture - should this be here. For now perhaps another small icon and rather than "John O'Nolan" is could say User or something of that ilk.

Expected behaviours:

* Based on other parts of ghost, the arrow should spin round and point up when menu drops down and then revert to pointing down when closed

* Clicking on anywhere away from menu should close the menu.


Options in drop-down menu:

* Your Profile - does nothing - should take you to a profile page or settings page

* Help/Support - does nothing - should take you to a help page or wiki

* Keyboard Shortcuts - does nothing - should take you to a shortcuts page or pop-up menu etc

* Sign Out - works and takes you back to log-in page


# Dashboard

Widgets drag and drop nicely although you cannot change your mind or undo your change, if that was possible it would be nice as resizing a box sometimes has side effects you aren't expecting and moves boxes you have previously styled. It would also be nice if you could 'fix' a box in place so that it cannot be affected by another box this way.

A couple of widgets do not have a settings icon in bottom right corner so they cannot be adjusted - not sure if that is a bug or on purpose. These currently are:

* Posts This Week (out of 20)

* Most Popular Posts

The Ghost Settings widget is bigger than it should be - the background image can be seen in the negative space separating the widgets directly below it. Hovering on this widget brings up an ugly orientation selection box which doesn't seem to be the correct dimensions (there is a top border and it feels as though it should have a bottom one as well or none at all?).  

Green tick in bottom right corner of widgets do nothing, it should save the current configuration and then close the settings box.

Refreshing page reverts back to initial configuration. i.e. the config is not being saved
It would be nice if there was a button/widget that allowed you restore the config to default or another saved config


# Content

Clicking on 'All Posts' drops down a menu with the options:

* All Posts - does nothing. 

* Recently Edited - does nothing

* By Author... - does nothing 

* Search... - does nothing


Expected behaviours:

* As with user menu, the arrow should spin round and point up when menu drops down and then revert to pointing down when closed

* Clicking on anywhere away from menu should close the menu.

Query - This drop down menu highlights as blue - very nice and the user menu highlights (or downlights) to a blackish colour. Should this be more consistent - Blue looks nice!

Green box with white addition symbol takes user to new post as expected.

On post preview pane the the star is empty for first post and has a hover effect but does nothing when clicked. Other posts have a filled star and a hover effect and still do nothing when clicked. The Text next to star says "PUBLISHED by JOHN O'NOLAN"  - this should either be refactored to a user profile or givena  generic name for now such as 'Published by User'. Note only the P and U are capitalised - if the whole word is capitalised then 'by' should be as well - otherwise it looks odd.

Selecting a post works.

# New Post

# Settings

 
## General tab

## Content

## Users

## Theme

## Connected Services

## Plugins
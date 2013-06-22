#Top Nav Bar

* G - highlights nicely on hover - is this supposed to have some function? Currently does nothing.
If there is currently no plan for this it would be nice if this took you to either the ghost website or a Ghost Foundation info page etc **Quick Win 1**

* Dashboard - takes to dashboard tab - working

* Content - takes to content tab - working

* New Post - takes to editor tab - working

* Settings -  takes to settings tab - working


### User drop-down menu

Who is the ugly git in the picture - should this be here. For now perhaps another small icon and rather than "John O'Nolan" is could say User or something of that ilk. **Quick Win 2**


Expected behaviours:

* Based on other parts of ghost, the arrow should spin round and point up when menu drops down and then revert to pointing down when closed **Quick Win 3**

* Clicking on anywhere away from menu should close the menu. **Quick Win 4**



Options in drop-down menu:

* Your Profile - does nothing - should take you to a profile page or settings page

* Help/Support - does nothing - should take you to a help page or wiki

* Keyboard Shortcuts - does nothing - should take you to a shortcuts page or pop-up menu etc **Quick Win 5**

* Sign Out - works and takes you back to log-in page


# Dashboard

Widgets drag and drop nicely although you cannot change your mind or undo your change, if that was possible it would be nice as resizing a box sometimes has side effects you aren't expecting and moves boxes you have previously styled. It would also be nice if you could 'fix' a box in place so that it cannot be affected by another box this way.

A couple of widgets do not have a settings icon in bottom right corner so they cannot be adjusted - not sure if that is a bug or on purpose. These currently are:

* Posts This Week (out of 20)

* Most Popular Posts


The Ghost Settings widget is bigger than it should be - the background image can be seen in the negative space separating the widgets directly below it **Quick Win 6**. Hovering on this widget brings up an ugly orientation selection box which doesn't seem to be the correct dimensions (there is a top border and it feels as though it should have a bottom one as well or none at all?).  

Green tick in bottom right corner of widgets do nothing, it should save the current configuration and then close the settings box.

Refreshing page reverts back to initial configuration. i.e. the config is not being saved
It would be nice if there was a button/widget that allowed you restore the config to default or another saved config.


# Content

### All Posts drop-down menu:

* All Posts - does nothing. 

* Recently Edited - does nothing

* By Author... - does nothing 

* Search... - does nothing


Expected behaviours:

* As with user menu, the arrow should spin round and point up when menu drops down and then revert to pointing down when closed

* Clicking on anywhere away from menu should close the menu.


Query - This drop down menu highlights as blue - very nice and the user menu highlights (or downlights) to a blackish colour. Should this be more consistent - Blue looks nice! **Quick Win 7**

Green box with white addition symbol takes user to new post as expected.

On post preview pane the the star is empty for first post and has a hover effect but does nothing when clicked. Other posts have a filled star and a hover effect and still do nothing when clicked. The Text next to star says "PUBLISHED by JOHN O'NOLAN"  - this should either be refactored to a user profile or givena  generic name for now such as 'Published by User'. Note only the P and U are capitalised - if the whole word is capitalised then 'by' should be as well - otherwise it looks odd. **Quick Win 8**

Selecting a post works.

Edit post icon works


### Settings Icon (blue highlights again - yay!)

Expected behaviours same as previous drop down menus

Current options are:

* URL - seems ambiguous - does nothing

* Something - seems like we don't know what we want - remove for now **Quick Win 9**

* Delete - works as expected


# New Post

Title - obvious from placeholder text

It takes 2 tabs to get from title to markdown - very irritating and simple to fix!
[Issue 153](https://github.com/TryGhost/Ghost/issues/153) **Quick Win 10**

Markdown - obvious
The ? icon does nothing
!image[] places the dropzone but you cannot add an image- for now would be nice to have the basic uploader js to give the VIPs an initial feeling with documented limitations (also makes it look like something that is road-mapped for later in year is well on its way!) **Quick Win 12**

Preview - obvious
Word Count seems to work

### Bottom nav bar

Pencil icon allow to type and enter saves word to toolbar with option to delete. Not sure what this is used for and settings Icon does nothing - Not sure it is needed here, seems like an overabundance of these icons. We could hide these for now **Quick Win 11**

Update post menu (Blue!) - all working or with appropriate alerts. Issues alerts [Issue #37](https://github.com/TryGhost/Ghost/issues/37) 


# Settings


Save button issues too many alerts  [Issue 174](https://github.com/TryGhost/Ghost/issues/174)


## General tab


Options

* Blog Title - saves and is used correctly

* Blog Logo - cannot change at the moment - a generic logo would be better for now

* Blog Icon - same as above

* Email Address - saves and is used correctly. "admin notifications" link nothing. Show my email address button does nothing at this stage.

* URL Structure - does nothing

* Time Zone - does nothing only 1 option




## Content

Only homepage description saves and is used

## Users

Too many O'Nolans

Nothing works here yet


## Theme

Horrid text not even english it may be klingon!


## Connected Services & Plugins


Empty page

Clicking on connected Services seems to highlight plugins as well and vice versa


# Quick Wins

1. Adding a link to the G in Nav Bar
2. Replace User menu pic and name
3. Make Menu icons spin
4. Close Menus when you click anywhere other than menu
5. Load a wiki page with shortcuts or a pop-up etc.
6. Fix image in ghost widget
7. Change User menu highlight to Blue - simple just depends on the personal choice of whether or not this is required
8. Change static content of 'Published By' on content preview panel
9. Remove the 'something' option from settings menu in content preview pane
10. Fix tab-indexing on New Post page
11. Hide pencil and settings icon on editor - bottom nav bar
12. Incorporate the basic image uploader JS - ready to go really.

_Other important fixes would be to remove the alerts for all save buttons but I am not sure how involved that is so not a listed as a Quick Win_


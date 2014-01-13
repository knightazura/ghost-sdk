_This release represents a total of **374** commits across **178** issues from **88** incredible contributors all over the world._

This version has focused heavily on refactoring Ghost, with a large number of non-user facing changes. These release notes detail only the features, fixes and changes that we consider will be of interest to most Ghost users. For those who are interested, the [full changelog](https://gist.github.com/ErisDS/8397171) is  available as a gist.

### New Features

*  static pages
*  unsaved changes notification
*  featured posts
*  sexy new loading bar
*  quick edit post URL
*  date based permalink support. 
*  subdirectory support
*  gravatar for user images
*  SSL support
*  welcome email on blog creation
*  available update notifications
*  tag helper has suffix and prefix property
*  new encode helper

### Noteworthy Changes

*  notifications are now bottom left
*  switch to busboy for uploads
*  switch to server side sessions
*  more secure password reset process
*  sort by publish date on content screen
*  time supported in published date
*  support for SVG images when uploading
*  swapped nodejs-bcrypt for bcryptjs

### Important bug fixes

*  duplicate content on content screen
*  content disappears after publishing
*  issues with partials and theme switching
*  email address is not case sensitive on signin
*  reversed post order on import
*  unicode characters in post slugs are converted to ascii	
*  unpublished posts are not accessible
*  no negative posts per page
*  content & excerpt helpers work with unicode characters
*  punctuation in titles not properly respected
*  preview pane in editor no longer editable


These are just a few highlights. The 0.4 release contains almost 100 minor bug fixes, including numerous fixes to styling, the markdown editor, admin interface behaviour, security, rss feeds and the Casper theme.

Ghost has also been refactored significantly, meaning the codebase is considerably improved. Some key areas of refactor work occurred around config loading and management, storage and retrieval of paths and URLs, the removal of the ghost.js file, cleanup work around the API and a complete re-write of the database migrations system.


Finally, there has also been significant advances in the test suite, including running tests against sqlite, mysql and pg, improvements to unit, functional and integration tests and the ability to generate a coverage report. This improved test suite makes it easier for us to move faster and deliver more features with confidence in the future.


## Notes on key features

A few of our new features are worthy of further explanation.

### Static pages

You can now toggle any post to be a "page" from within your post settings menu on the editor or content screen. This will remove it from your post feed. About / Contact / Terms galore!

### Unsaved changes notifications

We'll now give you a heads up when you're about to lose unsaved changes. So you can, you know, save.

### Featured posts

Clicking the star on the content screen will mark a post as featured. Featured posts get an extra class so they can be styled differently.

### Sexy new loading bar. 

Always know when Ghost is doing something, a little blue bar crawls across the screen to let you know!

### Quick edit post URL

You can now slap /edit/ on the end of any post URL and, boom, you're editing it.

### Date based permalink support. 

Available from the general settings menu, you can now get Ghost to output URLs in the format: `/:year/:month/:day/:slug/` rather than just `/:slug/`.

### Subdirectory support

You can now configure your URL in `config.js` to contain a subdirectory, such as `http://my-ghost-blog.com/blog/`.

## Credits

This release was lovingly crafted by Hannah Wolfe, Fabian Becker, Sebastian Gierlinger, John O'Nolan, Harry Wolff, Jacob Gable, William Dibbern, Jakob Gillich, Matthew Harrison-Jones, Michael Bradshaw, Zach Schneider, cobbspur, jamesbloomer, Dane Springmeyer, Sebastian Gräßl, Zach Geis, buddhamagnet, Benjamin Chodoroff, Daniel Hanson, Gabor Javorszky, Mark Berger, Matt DuVall, Patrick Garman, Seb Gotvitch, Tim Griesser, Tony Gaskell, b1nd, germanrcuriel, remixz, sjama, Ben Gladwell, Declan cook, Derek Myers, Devin Doolin, Enrique Chavez, Harry Walter, Henning Sprang, Jacob Kaplan-Moss, Jacques Marneweck, Jeff Escalante, Jonathan Johnson, Jono Warren, Jorge Niedbalski, Karl Mikkelsen, Karolis Dzeja, Kumar Abhinav, Lev Gimelfarb, Lucas, Luke Arduini, Manuel Gellfart, Matheus Azzi, Matt Florence, Matt Hughes, Matthew DuVall, Michael Nason, Micheil Smith, Nick Donohue, Nick Pfisterer, Nick Schonning, Pascal Borreli, Paul, Paul Adam Davis, Peter deHaan, Ryan Powell, Ryan Seys, Sean Hellwig, Simone D'Amico, StevenMcD, Talon, Thomas Faurbye Nielsen, Tim Mansfield, Tom Gillett, Vineet Sinha, WangSai, Will Glynn, William Golden, Zlatan Vasović, abe33, ali, andy matthews, danschumann, enahs, jtw, moritz haarmann, nason, nicovalencia, omeid and rektide.

**Thank you all!**
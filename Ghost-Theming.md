The aim overall is to make theming easier - having a clear divide between the templates (HTML and CSS) and business logic (JS) affords easier collaboration between designers & developers as well as making it easier to code due to separation of concerns - it's easier to know where things go.

So templates have data, and basic control structures such as loops, if statements and with context blocks.

Now, if the theme needs to manipulate the data it's getting from Ghost in order to display it (one example would be, to choose how you want to format a date) - we can do this with helpers. There will be a number of core helpers available. The vision is that a theme would include a helpers.js where any custom helpers are defined, or potentially core ones overridden / extended.

Where WordPress has wp_query() - Ghost has API requests and filters for those API requests. Filters are super powerful. Ghost can hand the theme/plugin developer a JavaScript object, and the developer can change this however they like (providing the result is valid). The JS object can just as easily represent the query to be done as the data which is the result. So, expect lots of well documented filter 'hooks' to use the wp term - and one very consistent way of doing this sort of thing.

The third thing in WP is actions - functions which get run at certain point and may or may not have data, but definitely doesn't operate on any output. I'm not yet convinced of the need for these when filters are so similar and so powerful. We will assess this as we go and only add then if there is an obvious and clear need and distinction

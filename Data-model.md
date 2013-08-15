(This is very much a work in progress)

**Global questions**: 
 * Should everything have a uuid?

**Questions**: 
 * Should we have a secondary meta data table like WP or allow plugins to actually add columns to the table? 
 * How can we allow for custom fields?
 * Do we need a 'type' field?
 * Should we have meta data columns on most major tables, or not?
 * What needs to be nullable?
 * What needs to be a 'string' vs 'text'
 * How are custom fields going to work?
 * What other data needs to be stored that isn't accounted for yet?

The current plan for the db lives at https://gist.github.com/ErisDS/cd0f3d33072410309f37

You can see all the changes so far, in reverse order by taking a look at the [revisions](https://gist.github.com/ErisDS/cd0f3d33072410309f37/revisions) of the gist.


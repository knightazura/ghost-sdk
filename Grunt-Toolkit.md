[coming soon]

## Building assets with `grunt` & `grunt init`

## Testing with `grunt validate`

`grunt validate` runs 3 sets of tests: jsLint, mocha unit tests and casperjs functional tests.

This can take a while, so it makes sense to run the individual sections if you're working on specific things.

- `grunt jslint` will run just the linter
- `grunt mochacli:all` will run all of the unit tests, `grunt mochacli:api` will run the data model unit tests which are incorrectly labeled api, see `mochacli` config in `Gruntfile.js` for a full set of the individual groups of tests which can be run and feel free to add your own.
- `grunt test functional` will run the functional tests

## Developing with `grunt watch` or `grunt dev`

## Generating docs with `grunt docs`

## Creating builds with `grunt build`

## Creating changelogs with `grunt changelog`
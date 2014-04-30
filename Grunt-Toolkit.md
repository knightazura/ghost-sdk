Ghost has a number of tasks which are automated via Grunt. The following document explains what each thing does. You can also get help when running grunt by typing `grunt --help`

## Building assets with `grunt` & `grunt init`

The default `grunt` task does two things: 
1. compile sass into css
2. compile the templates in `core/client/tpl` into the `hbs-tpl.js` file

These are commonly needed after pulling changes from master, so it's recommended to always do it after a pull as a matter of habit.

If you have a fresh repo and are running `grunt` for the first time, you'll need to run `grunt init` rather than just `grunt` as this also installs bourbon. This only has to be done once on a repo.

## Preparing to deploy into production with `grunt prod`

The `grunt prod` task goes one step beyond the default `grunt` task and minifies the Ghost JavaScript source for production via an additional [uglify](https://github.com/mishoo/UglifyJS2) task. The production assets are included in releases, this task is only needed for people running directly from GitHub 

## Testing with `grunt validate`

`grunt validate` runs all of Ghost's test suites: jshint, unit tests (mocha), integration tests (mocha with DB access), api functional tests (mocha) and interface functional tests (CasperJS).

This can take a while, so it makes sense to run the individual sections if you're working on specific things.

- `grunt jshint` - run just the linter
- `grunt test-unit` - run all of the unit tests, see `mochacli` config in `Gruntfile.js` for a full set of the individual groups of unit tests which can be run and feel free to add your own.
- `grunt test-integration` - run the database integration tests
- `grunt test-route` - run the route functional tests
- `grunt test-functional` - run the interface functional tests (both admin and theme). You can further specify which folder or file of functional tests you want to run by specifying a `--target`, e.g. `grunt test-functional --target=admin/`

## Generating a test coverage report with `grunt test-coverage`

A coverage report can be generated which takes into account all of the tests which run using mocha. The coverage report is not hooked into in Travis or any other automatic systems at present, but is used to regularly check the progress of testing in Ghost.

## Developing with `grunt watch` or `grunt dev`

Grunt watch and grunt dev are tools which will help to build Ghost assets whilst you are making changes to the files.

[More info needed...]

## Generating docs with `grunt docs`

Ghost has some inline documentation using markdown comments which can be generated using `grunt docs` definitive formatting / style have not yet been determined / documented.

## Creating releases with `grunt release`

The release task exists for the creation of correctly build and formatted release zips, this is used when releasing a new version of Ghost, but may also be used by packaging tools. The task ensures that all the assets are built and prepared, and that no extraneous files such as tests, configurations or customisations are included.

## Creating changelogs with `grunt changelog`

The changelog is generated using git tags and commit messages. A new tag must be added prior to running `grunt release` - a correctly formatted changelog will then be included in the release.
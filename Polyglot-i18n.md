So far we have node-polyglot installed & a config option which provides either "en" or "en_PL" languages. 

_e() equivalent syntax is:


```
#!hbs

{{e key defaultString options}}

```
Where:

* key is the lookup key to find the correct string in the language json files
* defaultString is the String in English (UK)
* options is any variables which require interpolation, in attribute="value" format

Simple example

```
#!hbs

{{e "editor.actions.save_draft" "Save Draft"}}
```


Example with interpolation


```
#!hbs

{{e "editor.word_count" "%{count} words" count="561"}}
```

The function is used in the navbar partial, and throughout editor.hbs as an example.

Still todo:

* ensure all of the admin is marked up [#16](https://github.com/TryGhost/Ghost/issues/16)
* move the i18n code to somewhere sensible [#17](https://github.com/TryGhost/Ghost/issues/17)
* optimise for the default "en" language [#18](https://github.com/TryGhost/Ghost/issues/18)
* use promises to load the language file [#21](https://github.com/TryGhost/Ghost/issues/21)

Also to be in separate stories:

* language file loading for the frontend / theme [19](https://github.com/TryGhost/Ghost/issues/19)
* using req.acceptedLanguages to set the language on first load of the dashboard after install [#20](https://github.com/TryGhost/Ghost/issues/20)


Interesting questions:

* should the admin i18n be in a json file, or should it be in the database?
* how can we make it easy for developers to create these files for their themes / plugins?
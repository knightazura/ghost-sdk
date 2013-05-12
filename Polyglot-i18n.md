So far we have node-polyglot installed & a config option which provides either "en" or "en_PL" languages.
_e() equivalent syntax is:

{{e key defaultString options}}
Where:

key is the lookup key to find the correct string in the language json files
defaultString is the String in English (UK)
options is any variables which require interpolation, in attribute="value" format
Simple example

{{e "editor.actions.save_draft" "Save Draft"}}
Example with interpolation

{{e "editor.word_count" "%{count} words" count="561"}}
The function is used in the navbar partial, and throughout editor.hbs as an example.

Still todo:

move the i18n code to somewhere sensible
optimise for the default "en" language
use promises to load the language file
Also to be in separate stories:

language file loading for the frontend / theme
using req.acceptedLanguages to set the language on first load of the dashboard after install
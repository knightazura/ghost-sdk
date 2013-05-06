![Ghost Architecture Overview](http://erisds.co.uk/ghost/GhostArchNoText.png)

This represents a rough overview of the vision for the core architecture of Ghost. The most important point being that the data model should:

1. Expose a public API which we consume internally, so that the API is as important to us as it will be to 3rd parties
2. Use a data abstraction layer / ORM so that we can provide SQLite as a default option but allow for upgrades to MySQL or other storage systems without difficulty.

This diagram deliberately does not reference how these components should be built, or any frameworks or libraries. Although we have a rough working system built on Express, using jugglingDB as the ORM and using handlebars for templating, each of these things is still up for discussion. Long term, we expect to turn more and more of the 3rd party libraries into core competencies by either forking the libraries or building our own.

The editor write screen is currently built using CodeMirror & Showdown. These are first candidates for being rewritten specifically for Ghost.
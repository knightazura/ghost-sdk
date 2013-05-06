![Ghost Architecture Overview](http://erisds.co.uk/ghost/GhostArchNoText.png)

This represents a rough overview of the vision for the core architecture of Ghost. The most important point being that the data model should:
1. Expose a public API which we consume internally, so that the API is as important to us as it will be to 3rd parties
2. Use a data abstraction layer / ORM so that we can provide SQLite as a default option but allow for upgrades to MySQL or other storage systems without difficulty.



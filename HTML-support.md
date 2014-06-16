HTML can be used to achieve results not available using Markdown's syntax. Simply use HTML tags.

There are restrictions on using block-level HTML elements — e.g. `<div>`, `<table>`, `<pre>`, `<p>`, etc. These
* must be separated from surrounding content by blank lines;
* must not be indented with tabs or spaces; and
* ignore any Markdown syntax, i.e. Markdown emphasis, links etc. cannot be used within such blocks.

There are no such restrictions on span-level HTML elements — e.g. `<span>`, `<cite>`, `<del>`, etc. Markdown syntax is processed within span-level tags.
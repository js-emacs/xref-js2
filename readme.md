# xref-js2

`xref-js2` adds navigation to definitions or references to JavaScript projects
in Emacs.

`xref-js2` adds an xref backend for JavaScript files.

Instead of using a tag system, it relies on `ag` to query the codebase of a
project.  This might sound crazy at first, but it turns out that `ag` is so fast
that jumping using `xref-js2` is most of the time instantaneous, even on fairly
large JavaScript codebases (it has been tested on 50k lines of JS code).

Because line by line regexp search has its limitations, `xref-js2` does a second
pass on result candidates and eliminates possible false positives using
`js2-mode`'s AST, thus giving very accurate results.

## Requirements

- Emacs 25.1
- `ag` (the [silver searcher](http://geoff.greer.fm/ag/))
- js2-mode

## Demo

![jump-to-definition.gif](screencasts/jump-to-definition.gif)
![jump-to-references.gif](screencasts/jump-to-references.gif)

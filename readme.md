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

## Installation

If you use `js2-mode`, `M-.` will be bound by `js2`, you might want to unbind it:

```
(define-key js2-mode-map (kbd "M-.") nil)
```

Then you need to add the xref backend:

```
(add-hook 'js2-mode-hook (lambda ()
  (add-hook 'xref-backend-functions #'xref-js2-xref-backend nil t)))
```

## Demo

### Jumping to definitions and back
![jump-to-definition.gif](screencasts/jump-to-definition.gif)

### Finding references
![jump-to-references.gif](screencasts/jump-to-references.gif)

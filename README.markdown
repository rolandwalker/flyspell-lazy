[![Build Status](https://secure.travis-ci.org/rolandwalker/flyspell-lazy.png)](http://travis-ci.org/rolandwalker/flyspell-lazy)

Overview
========

Improve Emacs flyspell responsiveness using idle timers.

Quickstart
----------

```lisp
(require 'flyspell-lazy)
 
(flyspell-lazy-mode 1)
 
(flyspell-mode 1)      ; or (flyspell-prog-mode)
```

flyspell-lazy
-------------

`flyspell-mode` has performance issues on some platforms.
Specifically, keyboard responsiveness may be significantly
degraded on OS X.

This package reduces the amount of work done by flyspell.  Instead
of checking *instantly* as you type, spelling will be checked when
the current buffer has been idle for a short time.  (Vanilla
`flyspell-mode` does not use idle timers but a subtle combination
of hooks and `sit-for`.)

This package also turns off `flyspell-mode` completely for certain
buffers.

To use this library, add the following to your ~/.emacs

```lisp
(require 'flyspell-lazy)
(flyspell-lazy-mode 1)
```

Then use `flyspell-mode` as you normally would.  This package does
not load flyspell for you.

`flyspell-lazy-mode` will invoke spellcheck less frequently than
vanilla `flyspell-mode`, though this can be changed somewhat via
`customize`.

Notes
-----

If you are using `aspell` instead of `ispell` on the backend, the
following setting may improve performance:

```lisp
(add-to-list 'ispell-extra-args "--sug-mode=ultra")
```

Compatibility and Requirements
------------------------------

	GNU Emacs version 24.3-devel     : yes, at the time of writing
	GNU Emacs version 24.1 & 24.2    : yes
	GNU Emacs version 23.3           : yes
	GNU Emacs version 22.3 and lower : no

No external dependencies

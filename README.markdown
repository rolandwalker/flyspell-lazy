[![Build Status](https://secure.travis-ci.org/rolandwalker/flyspell-lazy.png?branch=master)](http://travis-ci.org/rolandwalker/flyspell-lazy)

# Overview

Improve Emacs flyspell responsiveness using idle timers.

 * [Quickstart](#quickstart)
 * [Explanation](#explanation)
 * [Notes](#notes)
 * [Compatibility and Requirements](#compatibility-and-requirements)

## Quickstart

```elisp
(require 'flyspell-lazy)
 
(flyspell-lazy-mode 1)
 
(flyspell-mode 1)      ; or (flyspell-prog-mode)
```

## Explanation

This package is only useful if you are experiencing performance
issues with Emacs' built-in `flyspell-mode`.  Specifically, keyboard
responsiveness was significantly degraded on OS X before GNU Emacs
24.3.  See this (now resolved) bug:

<http://debbugs.gnu.org/cgi/bugreport.cgi?bug=2056>

This package reduces the amount of work done by flyspell.  Instead
of checking *instantly* as you type, spelling will be checked when
Emacs has been idle for a short time.  (Vanilla `flyspell-mode`
does not use idle timers but a subtle combination of hooks and
`sit-for`.)

This package also forces `flyspell-mode` off completely for certain
buffers.

To use this library, add the following to your `~/.emacs` file

```elisp
(require 'flyspell-lazy)
(flyspell-lazy-mode 1)
```

Then use `flyspell-mode` as you normally would.  This package does
not load flyspell for you.

`flyspell-lazy-mode` will invoke spellcheck less frequently than
vanilla `flyspell-mode`, though this can be changed somewhat via
`customize`.

## Notes

If you are using `aspell` instead of `ispell` on the backend, the
following setting may improve performance:

```elisp
(add-to-list 'ispell-extra-args "--sug-mode=ultra")
```

## Compatibility and Requirements

	GNU Emacs version 25.1-devel     : not tested
	GNU Emacs version 24.5           : not tested
	GNU Emacs version 24.4           : yes
	GNU Emacs version 24.3           : yes
	GNU Emacs version 23.3           : yes
	GNU Emacs version 22.2           : yes, with some limitations
	GNU Emacs version 21.x and lower : unknown

No external dependencies

## Why this fork? ##

This fork exists because fset fails on sbcl when safety is set to 3 - see [this discussion](https://github.com/slburson/fset/issues/100#event-21762548245).
As suggested by fset's author, Code/port.lisp has been modified, so that hash-mix/hash-unmix/hash-multiply use the generic branch in sbcl, i.e., the branch that uses XOR instead of addition. It currently passes the following:
```
rm -rf ~/.cache/common-lisp ; sbcl --non-interactive --eval "(progn (sb-ext:restrict-compiler-policy 'safety 3) (ql:quickload :FSet) (asdf:test-system :FSet))"
```

## Introduction ##

FSet is a functional set-theoretic collections library.  _Functional_ means that all
update operations return a new collection rather than modifying an existing one in
place.  _Set-theoretic_ means that collections may be nested arbitrarily with no
additional programmer effort; for instance, sets may contain sets, maps may be keyed
by sets, etc.

The [FSet home
page](https://gitlab.common-lisp.net/fset/fset/-/wikis/home) has an
introduction and tutorial.

There might be some useful information on the [FSet CLiki page](http://cliki.net/FSet).

FSet is installable via Quicklisp:

```
> (ql:quickload "fset")
```

I occasionally post FSet news to [my blog](https://scottlburson2.blogspot.com/).

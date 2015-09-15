<!-- 
.. title: Nikola v7.7.1 is out!
.. slug: nikola-v771-is-out
.. date: 2015-09-15 18:54:58 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
-->

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.7.1. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

About This Release
==================

This release focused in fixing bugs. We fixed so many, we have now **fewer than 10 bugs open!**

Also, we added a new tutorial to the website, about
[creating heavily customized pages](https://getnikola.com/creating-a-custom-page.html)
check it out, the [end result](https://getnikola.com/dr-nikola-final.html) is pretty cool!

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/vX.Y.Z
[PyPI]: https://pypi.python.org/pypi/Nikola/X.Y.Z

Changes
=======

Features
--------

* Better Template / JS / CSS demo in sample site.
* New normalize_html filter
* Support UTF-8 paths and encoded links when the ``USE_SLUGIFY`` option
  is disabled. (Issue #2037)
* Per-document hyphenation using "hyphenate" metadata flag.
* New option USE_KATEX to switch from MathJax to KaTeX (Experimental).
* Support SVG in galleries (Issue #1605)
* Made TAG_PATH translatable (Issue #1914)
* Made CATEGORY_PATH translatable (Issue #1914)
* Display post counts for archive links (Issue #2011)
* Document link/path handlers (Issue #2008)
* Made DATE_FORMAT and JS_DATE_FORMAT translatable (Issue #2032)

Bugfixes
--------

* Generate language-specific section links (Issue #2069)
* Rebuild pages when user changes POST_SECTION_COLORS (Issue #2066)
* Look for bundle assets also in output/, allowing bundling of files
  created by plugins (Issue #1370)
* In listings, if lexer is not specified, use literal (Issue #2078)
* Remove bogus ambiguity on listing links (Issue #2080)
* Unix-slash caused conflict in Windows (Issue #2079)
* Locale is now threadsafe, avoid races in threaded builds (Issue #2071)
* Make typogrify filter work when applied from metadata (Issue #2064)
* Handle metadata in post files that start with a BOM (Issue #2059)
* Handle error downloading bootswatches (Issue #2054)
* Monitor plugins/ in ``nikola auto`` (Issue #2044)
* Multi-lingual and multi-level directories confused section slug
  detection (Issue #2023)
* Use Unicode strings for WordPress comment headers (Issue #2019)
* Don't add stories to author pages (Issue #2007)

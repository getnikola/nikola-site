.. title: Nikola v7.8.0 is out!
.. slug: nikola-v780-is-out
.. date: 2016-08-29 12:50:41 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
.. author: Roberto Alsina

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.8.0. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.8.0
[PyPI]: https://pypi.python.org/pypi/Nikola/7.8.0

Changes
=======

Features
--------

* Exposed ``gist`` as a shortcode (Issue #2459)
* Always copy source files for listings (Issue #2473)
* Detect dependencies in template strings (Issue #2455)
* RSS feeds for sections (Issue #2068)
* New ``data`` metadata that loads data from external files (Issue #2450)
* Shortcode to escape to the template language (Issue #1227)
* Added link to raw file in listings (Issue #1995)
* New NO_DOCUTILS_TITLE_TRANSFORM (Issue #2382)
* Update options of chart directive to Pygal 2.2.3
* Pass global context to template shortcodes (Issue #2424)
* Added new options --html2text and --transform-to-markdown
  to WordPress importer (Issue #2261)
* Listing: guess the lexer if cannot be determined from the file name.
* Read files from data/ and insert data in global context (Issue #2477)

Bugfixes
--------

* Added link to sources in the output of listing directive (Issue #2472)
* Fix Windows crash with calendar locales (Issue #2332)
* Remove the (useless) ``<base>`` tag by default; change conf.py to
  opt in (Issue #2471)
* Show tag descriptions when TAG_PAGES_ARE_INDEXES is True (Issue #2444)
* Record template dependencies for post-list shortcut (Issue #2451)
* Default to English for docutils messages if no translations exist
  (Issues #2422, #2437)

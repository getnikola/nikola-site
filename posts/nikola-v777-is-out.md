.. title: Nikola v7.7.7 is out!
.. slug: nikola-v777-is-out
.. date: 2016-03-10 17:16:24 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.7.7. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.7.7
[PyPI]: https://pypi.python.org/pypi/Nikola/7.7.7

Changes
=======

Features
--------

* New ``--one-file`` option to wordpress importer (Issue #2262)
* New Pygal-based chart shortcode (Issue #2170)
* Add ``post_type`` to post-list directive (Issue #2272)
* Use ``sys.executable`` for launching pip in ``plugin`` (Issue #2275)

Bugfixes
--------

* Fix Indonesian translation (Issue #2291)
* Fix a JSON conversion bug in the WordPress importer (Issue #2264)
* Don’t create download directories when not downloading WordPress
  attachments (Issue #2260)
* Don’t display "Good link" messages in ``nikola check -l`` by default,
  can be re-enabled with ``-v`` option (Issue #2268)
* Fix a format string in ``nikola check`` (Issue #2267)
* Don't crash wordpress importer when posts are "empty" (Issue #2263)
* Don't put untranslated and nonexistent posts in sitemap (Issue #2289)


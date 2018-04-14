<!-- 
.. title: Nikola v7.6.2 is out!
.. slug: nikola-v762-is-out
.. date: 2015-07-29 18:18:31 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
-->

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.6.2. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/ (BTW, we totally rewrote the website, now it's modern and pretty!)

Downloads
=========

Get it on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.6.2
[PyPI]: https://pypi.python.org/pypi/Nikola/7.6.2

Changes
=======

Features
--------

* Make the Google Search example prettier, integrating well with
  Bootstrap 3 (Issue #1912)
* Add categories filter to post list directive (via Issue #1889)
* Remove empty directories with nikola check --clean-files (Issue #1873)

Bugfixes
--------

* Don't assume things are HTML in auto mode (Issue #1915)
* Don’t rebuild Atom syndication files unnecessarily often
* Include .php files in sitemaps
* Retry all client errors (4xx) to HEAD as GET request when checking remote links
* Graceful fallback in ``nikola serve --detach`` on Windows (Issue #1913)
* Don't auto-rebuild on changes to ".foo" or "foo~" or changes in folders
* auto should also rebuild in response to move events
* Don’t get metadata from file if compiler-specific metadata exist (Issue #1904)
* Fix PRETTY_URLS prompt for Windows (Issue #1901)
* Fix reST and Markdown title extraction from documents (Issue #1895, #1898)
* Minor improvements to the extending document
* Re-add the hack to kill nikola auto on ^C (Issue #1893)



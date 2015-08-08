<!-- 
.. title: Nikola v7.6.3 is out!
.. slug: nikola-v7.6.3-is-out
.. date: 2015-08-08 14:12:36 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
-->

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.6.3. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.6.3
[PyPI]: https://pypi.python.org/pypi/Nikola/7.6.3

Changes
=======

Features
--------

* New translations: Serbian and Bosnian, by saleone
* Added mechanism for rest extensions to depend on configuration options
  (Issue #1919)
* Render Jupyter notebooks (ipynb) in listings (Issue #1900)

Bugfixes
--------

* Handle folders without trailing slashes in nikola auto (Issue #1933)
* Set a base element to aid relative URL resolution, stripped on-the-fly
  when using the auto or serve command to view site locally. (Issue #1922)
* Rebuild archives when post slugs and titles change (Issue #1931)
* Handle special characters in URLs in nikola auto (Issue #1925)
* Avoid Broken Pipe error in nikola auto (Issue #1906)
* "nikola auto" serving implicit index.html with wrong mime type (Issue #1921)
* Handle non-integer shutter speeds and other variables in WordPress
  importer (Issue #1917)


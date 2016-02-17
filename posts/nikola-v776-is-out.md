.. title: Nikola v7.7.6 is out!
.. slug: nikola-v776-is-out
.. date: 2016-02-17 18:47:19 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.7.6. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

This is a bugfix release, fixing a critical error in version 7.7.5's support for IPython/Jupyter notebooks.
If you had upgraded Nikola to version 7.7.5 and suddenly got errors or empty pages for your notebooks, 
upgrade to 7.7.6 and run `nikola build -a` to get everything in order.

Really sorry!


Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.7.6
[PyPI]: https://pypi.python.org/pypi/Nikola/7.7.6

Changes
=======

Features
--------

* Add ``FRONT_INDEX_HEADER`` setting to allow adding greeting notices
  to the main index page (Issue #2249)

Bugfixes
--------

* Make Jupyter posts build (Issues #2248, #2252)


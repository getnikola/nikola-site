<!-- 
.. title: Nikola v7.6.4 is out!
.. slug: nikola-v764-is-out
.. date: 2015-08-22 09:18:54 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
-->

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.6.4. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.6.4
[PyPI]: https://pypi.python.org/pypi/Nikola/7.6.4

Changes
=======

Features
--------

* Checking remote links also checks redirects (nikola check -lr)
* Update suggested license to its latest version (Issue #1950)
* Add Punjabi language, by Jasdeep Singh (Issue #1940)
* New option to use custom, and several ``TEASER_END`` values

Bugfixes
--------

* Rewrite srcset links (Issue #1939)
* Add dependencies for include tag in Mako (Issue #1956)
* Don’t duplicate BLOG_TITLE in the front page title (Issue #1952)
* Escape instad of strip HTML in titles (Issue #1952)
* Make LINK_CHECK_WHITELIST apply to remote link checks
* Make STORY_INDEX work together with PRETTY_URLS (Issue #1949)
* Refactor new_post to match lazy plugin loading (Issue #1943)
* Make Nikola startup faster by not loading useless plugins (Issue #1825)
* Ignore sliced multibyte characters when reading metadata for sitemaps
* Fix NameError caused by failed import in auto plugin.


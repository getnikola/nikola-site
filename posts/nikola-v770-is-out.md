<!-- 
.. title: Nikola v7.7.0 is out!
.. slug: nikola-v770-is-out
.. date: 2015-09-03 16:10:58 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
-->

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.7.0. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: https://getnikola.com/

Key Changes since v7.6.4
========================

* [Sections](https://getnikola.com/blog/new-feature-in-nikola-sections.html) by Daniel Aleksandersen
* Author pages by Juanjo Conti

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.7.0
[PyPI]: https://pypi.python.org/pypi/Nikola/7.7.0

Changes
=======

Features
--------

* New support for online CSS and JS minifying services (Issue #1999)
* Make <base> tag optional with USE_BASE_TAG flag (Issue #1985)
* Render author pages (Issue #1972)
* Atom feeds for tag lists (Issue #1686)
* New ``THEME_COLOR`` option for customizing themes from a primary color
  (Issue #1980)
* New ``color_hsl_adjust_hex`` and ``colorize_str_from_base_color``
  functions available in themes (Issue #1980)
* New ``POSTS`` output subfolders now generate sections by deault
  (Issue #1980)
* New ``POSTS_SECTIONS`` and ``POSTS_SECTION_*`` options for
  configuring the section pages (Issue #1980)
* For themers: Each ``post`` are now asssociated with section_color,
  section_link, and section_name (Issue #1980)
* Each new section page has a auto-assigned color based on shifting
  the hue of ``THEME_COLOR`` based on a hash of the section name,
  can be overwritten with ``POSTS_SECTION_COLORS`` option (Issue #1980)
* New ``TAG_PAGES_TITLES`` and ``CATEGORY_PAGES_TITLES`` options
  (Issue #1962)
* Add Bosnian and Serbian (Latin) languages, by Saša Savić [bs, sr_latin]
* Add Portuguese (Portugal) language, by jamatos [pt]

Bugfixes
--------

* Make nikola tabcompletion work outside sites (Issue #1983)
* Fix display of categories list in bootstrap theme (Issue #2002)
* If webassets is not installed, use unbundled assets (Issue #1992)
* Check links in Atom and sitemap files (Issue #1993) 
* Link checker should check all absolute URLs to self (Issue #1991) 
* Check ``img|source[@srcset]`` as part of ``check -l``  (Issue #1989)
* Clean up translations for third party components
* ``pagekind["main_index"]`` set on the main indexes to differentiate
  them from all the other indexes.
* Add dependency on metadata file for 2-file posts (Issue #1968)
* Set UTF-8 charset in Content-Type or text/* and *+xml (Issue #1966)


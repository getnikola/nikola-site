.. title: Nikola v7.8.5 is out!
.. slug: nikola-v785-is-out
.. date: 2017-05-12 12:50:41 UTC
.. tags: nikola, planet, python, programming, release
.. category: 
.. link: 
.. description: 
.. type: text
.. author: Roberto Alsina

On behalf of the Nikola team, I am pleased to announce the immediate availability of Nikola v7.8.5. It fixes some bugs and adds new features.

What is Nikola?
===============

Nikola is a static site and blog generator, written in Python.
It can use Mako and Jinja2 templates, and input in many popular markup formats, such as reStructuredText and Markdown — and can even turn Jupyter (IPython) Notebooks into blog posts! It also supports image galleries, and is multilingual. Nikola is flexible, and page builds are extremely fast, courtesy of doit (which is rebuilding only what has been changed).

Find out more at the website: <https://getnikola.com/>

Downloads
=========

Install using `pip install Nikola` or download tarballs on [GitHub][] and [PyPI][].

[GitHub]: https://github.com/getnikola/nikola/releases/tag/v7.8.5
[PyPI]: https://pypi.python.org/pypi/Nikola/7.8.5

Changes
=======

Math support changes
--------------------

* If you edited templates related to indexes and posts (``index.tmpl``,
  ``post.tmpl``, ``index_helper.tmpl``, ``post_helper.tmpl``) in your
  templates, you should adjust them to use ``math_helper.tmpl``.
* If you are using KaTeX, you should remove the CSS snippet from your
  configuration (templates), as that is now handled by Nikola.

Features
--------

* Get rid of ``THEME_REVEAL_CONFIG_*`` settings, use global context
  instead (Issue #2485)
* New emoji shortcode
* Add ``SECTION_PATH`` support to move the section indexes to a
  user-defined location (Issue #2738)
* Add a list of template variables to documentation (Issues #2328,
  #2712, #2259) and update the theming reference (Issue #2259)
* Add ``{post_title}`` tag for Read More links (Issue #2709)
* Include MathJax config only when needed (via Issue #2715)
* Include KaTeX CSS automatically when needed (Issue #2715)
* Split out math code into new ``math_helper.tmpl`` template (Issue
  #2715)
* Added ``jpegoptim_progressive`` filter to convert jpeg images to progressive
  jpegs.

Bugfixes
--------

* Open ``127.0.0.1`` when using ``nikola serve -b`` and default
  ``0.0.0.0`` hostname to avoid resolution issues — the site is still
  available on all interfaces (Issue #2755)
* Don't break animated GIFs in postprocessing (Issue #2750)
* More robust shortcodes, no need to escape URLs in reSt, work better
  with LaTeX, etc.
* No longer creates empty subarchive pages, and no longer create broken
  archive navigation links on day level (Issue #2734)
* Fixes post scanner plugin order (Issue #2720)
* Rename ``POSTS_SECTION_ARE_INDEXES`` to ``POSTS_SECTIONS_ARE_INDEXES``
* Make date ranges work in shortcode-based post lists (Issue #2690)
* Read data files only if Nikola configuration exists (Issue #2708)
* Make ``PAGE_INDEX`` work with ``PRETTY_URLS`` (Issue #2705)
* Fix PHP posts/pages not rendering on Windows (Issue #2706)
* Improving support for PostScanner plugins by asking them which compilers
  are unused (Issue #2496)


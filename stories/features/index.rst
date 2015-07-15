.. title: Features
.. slug: index
.. date: 2015-07-10 15:34:49 UTC
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

.. class:: alert alert-info
.. contents::


.. raw:: html

    <div class="feature-icon feature-icon-static pull-left">
    <a href="/features/static.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-server fa-stack-1x fa-inverse"></i>
    </span></a></div>

Static sites
============

Static websites are safer, use fewer resources, and avoid vendor and platform
lock-in. You can host a Nikola website on any web server, big or small. It’s
just a bunch of HTML files and assets.

`Explore in depth » </features/static.html>`__

.. raw:: html

    <div class="feature-icon feature-icon-fast pull-left">
    <a href="/features/fast.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-bolt fa-stack-1x fa-inverse"></i>
    </span></a></div>

Incremental builds
==================

Nikola is fast. We use `doit <http://pydoit.org/>`_, which provides incremental
rebuilds — in other words, we rebuild only the pages that need rebuilding,
saving CPU time, wall clock time and upload bandwidth.

`Explore in depth » </features/fast.rst>`__

.. raw:: html

    <div class="feature-icon feature-icon-input pull-left">
    <a href="/features/input.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-file-text fa-stack-1x fa-inverse"></i>
    </span></a></div>

Multiple input formats
======================

Nikola will take input in many formats. Out of the box, we support
reStructuredText, Markdown, IPython (Jupyter) Notebooks and HTML, and have
plugins for many other formats.

`Explore in depth » </features/input.html>`__

.. raw:: html

    <div class="feature-icon feature-icon-components pull-left">
    <a href="/features/components.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-cubes fa-stack-1x fa-inverse"></i>
    </span></a></div>

Built-in components
===================

Nikola comes with everything you need to build a modern website: blogs (with
comments, tags, categories, archives, RSS/Atom feeds), multilingual support,
easy image galleries, and code listings.

`Explore in depth » </features/components.html>`__

.. raw:: html

    <div class="feature-icon feature-icon-extensible pull-left">
    <a href="/extending.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-code fa-stack-1x fa-inverse"></i>
    </span></a></div>

Extensible
==========

Nikola is extensible. You can write a plugin to add any feature you want in a
few lines of Python, or write your own theme in Mako or Jinja2. Or find
something in the `Plugin <https://plugins.getnikola.com/>`__ and `Theme <http://themes.getnikola.com/>`__ Indexes.

`Read the extending documentation » </extending.html>`__

.. raw:: html

    <div class="feature-icon feature-icon-cli pull-left">
    <a href="/features/cli.html"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-terminal fa-stack-1x fa-inverse"></i>
    </span></a></div>

Friendly CLI
============

Nikola has a friendly user interface that gets you up and running quickly and
simplifies your work. You do not need to memorize headers just to create a post
— we’ll write them for you.

`Explore in depth » </features/cli.html>`__

.. raw:: html

    <div class="feature-icon feature-icon-coil pull-left">
    <a href="https://coil.readthedocs.org/"><span class="fa-stack fa-3x">
      <i class="fa fa-circle fa-stack-2x"></i>
        <i class="fa fa-users fa-stack-1x fa-inverse"></i>
    </span></a></div>

Coil CMS — a CMS for Nikola
===========================

If you want to use Nikola for a website that has content authored by people who
do not like command-line interfaces or who would prefer to use a WYSIWYG
editor, we have a solution for you.

Coil CMS is a basic CMS (with user management and a WYSIWYG HTML editor), which
uses Nikola to generate the pages, combining the best of both worlds: you (or
your editors) can easily create content, while the site is based on resilient
static pages.  Users don’t even have to know what Nikola, Python or static websites
are.  They just write their content.  The only difference is that they (or
someone with the necessary permissions) need to click a *Rebuild* button to
make their changes show up on the website.

`Read Coil CMS documentation » <https://coil.readthedocs.org/>`__

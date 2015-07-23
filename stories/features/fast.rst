.. title: Fast
.. slug: fast
.. date: 2015-07-10 15:38:40 UTC
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

.. class:: lead

Thanks to `doit <http://pydoit.org>`_, Nikola builds are incremental, which makes them extremely fast.

Nikola rebuilds only the files that *need* rebuilding — in other words, all the assets (JS, CSS) and older posts are left in place. Incremental rebuilds save CPU time, wall clock time and upload bandwidth (rsync will only upload some of the files).

.. contents::

Speed test: Average build times (in seconds)
============================================

`Speed test <https://chriswarrick.com/blog/2015/07/23/ssg-speed-test/>`_ performed by Chris Warrick on 2015-07-23:

.. raw:: html

    <table class="table table-bordered table-hover">
    <thead>
    <tr>
    <th>#</th>
    <th>Generator</th>
    <th>Average of 11 runs (with fresh build)</th>
    <th>Average of 10 runs (rebuilds only)</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th scope="row">1</th>
    <td>Nikola</td>
    <td>2.38290</td>
    <td>2.06057</td>
    </tr>
    <tr>
    <th scope="row">2</th>
    <td>Pelican</td>
    <td>2.61924</td>
    <td>2.62352</td>
    </tr>
    <tr>
    <th scope="row">3</th>
    <td>Hexo</td>
    <td>6.27361</td>
    <td>6.21267</td>
    </tr>
    <tr>
    <th scope="row">4</th>
    <td>Octopress</td>
    <td>9.57618</td>
    <td>9.47550</td>
    </tr>
    </tbody>
    </table>

Full results and methodology
----------------------------

Full results are available in `ods format <https://chriswarrick.com/pub/ssg-test-results.ods>`_. The methodology was described in the post about the results on `Chris Warrick’s blog <https://chriswarrick.com/blog/2015/07/23/ssg-speed-test/>`_.

Real life example
=================

When Nikola is run, it lists all the tasks that are run, with all the file names.

Let’s create an empty site:

.. listing:: build-logs/empty-site/0-fresh.txt console

As you can see, many files are created.  We create the resources for galleries, indexes, archives, listings, tags/categories, RSS, sitemaps, robots.txt, and assets (CSS/JS).

Let’s try building again:

.. listing:: build-logs/empty-site/1-nochanges.txt console

Nothing was changed.  Let’s add a new post:

.. listing:: build-logs/empty-site/post-1.txt console

Only a handful of files were changed or created this time.  Nikola created/updated archives, tag/category pages, tag cloud data, post sources, post pages, indexes, RSS and sitemaps.  A lot of things were left untouched, including the assets.

Let’s try one more post:

.. listing:: build-logs/empty-site/post-2.txt console

The list is pretty similar.  The archives page links to years, so it did not have to be changed.  The first post was changed to add a link to the second one.  Note that the tag page for *foo* was left untouched, the new post does not use it.

Let’s try a third post:

.. listing:: build-logs/empty-site/post-3.txt console

Once again, the other tags were not rebuilt, and the first post did not need changing.

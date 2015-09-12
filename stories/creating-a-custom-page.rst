.. title: Creating a Custom Page
.. slug: creating-a-custom-page
.. date: 2015-09-12 16:20:30 UTC
.. tags: tutorial
.. type: text
.. author: Roberto Alsina

The Nikola team tries very hard to make Nikola be simple, in a very specific way:

Once the user has things setup, doing the same thing again should take no work.
So, if you have done one image gallery, doing a second one should be just creating
a folder and putting images in it. If you have written a blog post, writing a new
one is running one command and editing the text you want to publish. And so on.

But sometimes, you don't want to do the same thing you have been doing. Sometimes you
want to make a one-off, a special thing, and Nikola should not get in the way
of you doing that. Rather, it should let you get your hands as dirty as you want.

So, this tutorial is about how to create a page that is totally different from all the
other pages in your site. A custom page.

Our goal for today is to make a page where it's nice to read a book. Specifically,
a book of late Victorian fiction called "Dr. Nikola's Vendetta" [1]_ because, how
could we resist using that one, right? And to make it maintain, within reason,
the "style" of the original book.

It's the first in a series of five books about Dr. Nikola, one of the first
recognizable archvillains, and ... well, they are not all that great, but they
are available at `Project Gutenberg <http://www.gutenberg.org/ebooks/author/3587>`__
and `Open Library <https://openlibrary.org/search?q=guy+boothby>`__ if you
want to read them.

The Open Library has `a lovely scan <https://archive.org/stream/bidforfortunenov00bootiala#page/n9/mode/2up>`__
of the original book we can use for some design guidance. On the other hand,
Project Gutenberg has `the text <http://www.gutenberg.org/ebooks/21640>`__
which we can use for actual content!

So, I took the prologue of the book, did some very light editing to turn it into
reStructuredText, added a picture of Dr. Nikola himself I found on Wikipedia,
and put it here for display. `Behold! <link://slug/dr-nikola-v1>`__

That is very... bad? While Nikola does the job, the default template is simply not
meant for this sort of thing.

The problems are many, from a book-reading point of view:

1) The column is too wide
2) The typesetting is all wrong
3) The sans-serif font is a very wrong idea for book material
4) it's so ... long!

So, let's fix them!

Custom Template
---------------

Like all pages, that one is shown using ``story.tmpl``:

.. listing:: story.tmpl html+mako

That has a lot of code in it that we don't really need. We know there will be no math here, and
I don't want comments on a book. Also, I saw a `nice tutorial about columns in CSS <https://css-tricks.com/guide-responsive-friendly-css-columns/>`__ so I want to style things up a little.

So, I will create a ``templates/book.tmpl`` in my site, and make this story use that by setting the
template metadata in the page to use it::

    .. template:: book.tmpl

Here is my new ``book.tmpl``:


.. listing:: book1.tmpl html+mako

And here is `the resulting page <link://slug/dr-nikola-v2>`__

What has changed?

1) I added a ``extra_head`` block. That goes, surprisingly, inside the ``HEAD`` element of the page, so
   it's a good place to add CSS that's specific to this page.

2) I removed unneeded parts of the content block, and moved the content around a little.

3) To create the nice responsive 1-or-2 column layout, I had to wrap the content in a few divs, one
   with columns, one that scrolls, one that has overflow hidden.

It's better, but it's far from awesome. So, let's continue!

Typesetting
-----------

Paragraph layout: Fiction books that are not fully justified feel wrong to me. So we should set
``text-align: justify;`` in the CSS. But to achieve proper justification, you also need hyphenation.
To have that in Nikola, you need to either enable it for the whole site (maybe not a great idea) or
just for this page using the hyphenate metadata::

    .. hyphenate: yes

Also, the original book has no space between paragraphs, and has bleeding in the first line, so more
CSS tweaks.

Proper “quotes”! And —dashes—! Nice, curly quotes are a must. Nikola has the typogrify filter to achieve that. Again,
you can enable it for your whole site, or just for this page using metadata::

    .. filters: filters.typogrify

Choosing the right font for a page or a site is an art. One I suck at, so I just went with a font that
was similar to the one used in the original book. There are a number of those, but I chose
`Gentium Basic <https://www.google.com/fonts/specimen/Gentium+Basic>`__. You can, of course, choose whatever
you want. Using it via Google Fonts is very simple.

Even with the nicer font, and the dual columns, the font size is too small, there is too many letters
per line. We *could* tweak that using CSS font sizes, but let's go crazy and use a Javascript solution:
`FlowType.JS <http://simplefocus.com/flowtype/>`__

Why FlowType.JS? It dynamically adjust the font size so that columns always have the right font size for
their width. That's just nice. To do that, we need to add JQuery and run a little JS in a ``<script>``
tag at the end of the page.

For that, the template offers the ``extra_js`` block. Since the bootstrap3 theme we are using already
loads JQuery, there is no need to do that, so it's just a matter of loading FlowType.JS and
initializing it:

.. code:: javascript+mako

    <%block name="extra_js">
        <script src="//cdnjs.cloudflare.com/ajax/libs/Flowtype.js/1.1.0/flowtype.min.js"></script>
        <script>
            $('#scrolling-cont').flowtype({
                minimum: 500,
                maximum: 1200,
                minFont: 20,
                maxFont: 40,
                fontRatio: 50
            });
        </script>
    </%block>

Figures: figures and multicolumn layout don't go along very well, they may even get split between columns!
The easiest solution is to make them fit in a "page", so, some more CSS for that.

Also, minor things like styling titles, subtitles, making the 1st word in the section smallcaps, and so on,
but hey, this is just CSS tweaking, we could do this forever.

So, here is our second attempt at a "book-like" template:

.. listing:: book2.tmpl html+mako

And here's our `much more nicely typeset book <link://slug/dr-nikola-v3>`__.

Interaction
-----------

Pages are not just text anymore. They need to interact with the user in the right way.
In this case, the scrolling horizontally to read another page is horrible:

* It's hard to stop at the right place
* You end up between pages 99% of the time

So, let's fix that with a little more JS at the end of the template:

.. code:: javascript

        $('#scrolling-cont').flowtype({
            minimum: 500,
            maximum: 1200,
            minFont: 20,
            maxFont: 40,
            fontRatio: 50
        });
        $(document).ready(function() {
            var elem = $('#scrolling-cont');
            elem.click(function(event) {
                var x1 = elem.position().left;
                var pw = elem.width() + 20;
                var x2 = event.pageX;
                if (x2 - x1 < pw / 2) {
                    pw = -pw;
                }
                elem.animate({
                    scrollLeft: '+=' + pw
                }, 500)
            });
        });

If you click on the right half of the book, it moves 2 pages to the right. If you click on the left half
it moves two pages to the left. Improvements are left as exercise to the reader, but please share!

And here's the final result: `A Bid For Fortune; Or; Dr. Nikola's Vendetta <link://slug/dr-nikola-final>`__

------------

.. [1] Sadly, the title is actually "A Bid For Fortune" and "Dr. Nikola's Vendetta"
       is the subtitle, but it works for me.

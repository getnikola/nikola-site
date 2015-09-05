.. title: Author pages in Nikola v7.7.0
.. author: Juanjo Conti
.. slug: author-pages-in-nikola-v770
.. date: 2015-09-04 16:08:03 UTC-03:00
.. tags: nikola, authors
.. category: Features
.. link:
.. description:
.. type: text

Since version 7.7.0 Nikola renders author pages for sites with more than one author.
Let me talk a little about this.

The first Nikola site I set up was for a group of friend wanting to publish tech
stuff online (for example, how to build a 3D printer with recycled elements).
I noticed that author names in posts weren't linked to any page. And because this is
a very common feature in blogging systems, I implemented it.

The feature can be enabled in `conf.py` with:

.. code-block:: python

    ENABLE_AUTHOR_PAGES = True

As with tags, you can configure the pages path and if you want to list links to the posts
or the posts themselves:

.. code-block:: python

    AUTHOR_PATH = "reporters"
    AUTHOR_PAGES_ARE_INDEXES = False

Additionaly, this is not required, you can add a little bio to each (or some) authors
and hide others (this is, don't generate pages for them):

.. code-block:: python

    AUTHOR_PAGES_DESCRIPTIONS = {
        DEFAULT_LANG: {
            "Juanjo Conti": "Python coder and writer.",
            "Roberto Alsina": "Nikola father."
        },
    }
    HIDDEN_AUTHORS = ['Guest']

If you want to link to these pages in your own theme, you can use something like this
(Mako example):

.. code-block:: mako

            % if author_pages_generated:
                <a href="${_link('author', post.author())}">${post.author()}</a>
            % else:
                ${post.author()}
            % endif

You can see the feature in action in `Nikola blog <https://getnikola.com/blog/>`_:
`author page example <https://getnikola.com/authors/roberto-alsina.html>`_,
`all authors page example <https://getnikola.com/authors/>`_.

Hope you enjoy it!

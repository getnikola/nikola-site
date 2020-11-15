.. title: Automating Nikola rebuilds with GitHub Actions
.. slug: automating-nikola-rebuilds-with-github-actions
.. date: 2020-04-24 22:24:48 UTC
.. tags: GitHub Actions, GitHub, automation, tips
.. author: Chris Warrick
.. type: text

In this guide, we’ll set up GitHub Actions to rebuild a `Nikola <https://getnikola.com/>`_ website and host it on GitHub Pages.

Why?
----

By using GitHub Actions to build your site, you can easily blog from anywhere
you can edit text files. Which means you can blog with only a web
browser and `GitHub.com <https://github.com>`_.
You also won’t need to install Nikola and Python to write. You won’t need a
real computer either — a mobile phone could probably access GitHub.com and write something.

Caveats
-------

* The build might take a couple minutes to finish (1:30 for the demo site;
  YMMV)
* When you commit and push to GitHub, the site will be published
  unconditionally. If you don’t have a copy of Nikola for local use, there is
  no way to preview your site.

What you need
-------------

* A computer for the initial setup that can run Nikola. You can do it with any
  OS (Linux, macOS, \*BSD, but also Windows).
* A GitHub account (free)

Setting up Nikola
-----------------

Start by creating a new Nikola site and customizing it to your liking. Follow
the `Getting Started guide <https://getnikola.com/getting-started.html>`_. You
might also want to add support for `other input formats
<https://getnikola.com/handbook.html#configuring-other-input-formats>`_, namely
Markdown, but this is not a requirement.

After you’re done, you must configure `deploying to GitHub
<https://getnikola.com/handbook.html#deploying-to-github>`_ in Nikola. There
are a few important things you need to take care of:

* Make your first deployment from your local computer and make sure your site
  works right. Don’t forget to set up ``.gitignore``.
* The ``GITHUB_COMMIT_SOURCE`` and ``GITHUB_REMOTE_NAME`` settings are
  overridden, so you can use values appropriate for your local builds.
* Ensure that the correct branch for GitHub Pages is set on GitHub.com.

If everything works, you can make some change to your site (so you see that
rebuilding works), but don’t commit it just yet.

Setting up GitHub Actions
-------------------------

Next, we need to set up GitHub Actions. This is really straightforward.

On your source branch, create a file named ``.github/workflows/main.yml`` with the following contents:

.. listing:: github-workflow.yml yaml
   :linenos:

There might be a newer version of the action available, you can check the
latest version in the `getnikola/nikola-action repo on GitHub
<https://github.com/getnikola/nikola-action>`_.

By default, the action will install the latest stable release of ``Nikola[extras]``. If you want to use the bleeding-edge version from ``master``, or want to install some extra dependencies, you can provide a ``requirements.txt`` file in the repository.

Commit everything to GitHub:

.. code:: console

   git add .
   git commit -am "Automate builds with GitHub Actions"

Hopefully, GitHub will build your site and deploy. Check the Actions tab in
your repository or your e-mail for build details. If there are any errors, make sure you followed this guide to the letter.

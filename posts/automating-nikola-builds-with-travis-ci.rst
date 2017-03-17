.. title: Automating Nikola rebuilds with Travis CI
.. slug: automating-nikola-rebuilds-with-travis-ci
.. date: 2016-08-24 18:05:25 UTC
.. updated: 2017-03-17 17:15:00 UTC
.. tags: Travis CI, GitHub, automation, tips
.. author: Chris Warrick
.. type: text

In this guide, we’ll set up Travis CI to rebuild a `Nikola
<https://getnikola.com/>`_ website and host it on GitHub Pages.

Why?
----

By using Travis CI to build your site, you can easily blog from anywhere
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

* A computer for the initial setup that can run Nikola and the Travis CI
  command-line tool (written in Ruby) — you need a Unix-like system (Linux,
  macOS, \*BSD, etc.); Windows users should try *Bash on Ubuntu on Windows*
  (available in Windows 10 starting with Anniversary Update) or a Linux virtual machine.
* A GitHub account (free)
* A Travis CI account linked to your GitHub account (free)

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
  works right. Don’t forget to set up ``.gitignore`` (We’ll add two **very**
  important entries later.)
* You must set ``GITHUB_COMMIT_SOURCE = False`` — otherwise, Travis CI will go
  into an infinite loop.
* We assume your source branch is ``src`` and you deploy to ``master``. Any
  other configuration requires editing ``.travis.yml``.
* We enable builds only for the ``src`` branch by default. Older versions of
  the script did not include this provision, and thus committing to ``master``
  (which you should not do, as your changes will be overwritten on next Travis
  rebuild) used to cause ``Rakefile`` errors.

If everything works, you can make some change to your site (so you see that
rebuilding works), but don’t commit it just yet.

Setting up Travis CI
--------------------

Next, we need to set up Travis CI. To do that, make sure you have the ``ruby``
and ``gem`` tools installed on your system. If you don’t have them, install
them from your OS package manager.

First, download/copy the ``.travis.yml`` file (note the dot in the beginning;
the downloaded file doesn’t have it!)
and adjust the real name, e-mail (used for commits; line 12/13), and the
username/repo name on line 21. If you want to render your site in another
language besides English, add the appropriate Ubuntu language pack to the list
in this file. Likewise, if you need any other Python/apt packages to build your
site, add them to your config.

.. listing:: travis.yml python
   :linenos:

Next, we need to generate a SSH key for Travis CI.

.. code:: console

   echo id_rsa >> .gitignore
   echo id_rsa.pub >> .gitignore
   ssh-keygen -C TravisCI -f id_rsa -N ''

Open the ``id_rsa.pub`` file and copy its contents. Go to GitHub → your page
repository → Settings → Deploy keys and add it there. Make sure *Allow write
access* is checked.

And now, time for our venture into the Ruby world. Install the ``travis`` gem:

.. code:: console

   gem install --user-install travis

You can then use the ``travis`` command if you have configured your ``$PATH``
for RubyGems; if you haven’t, the tool will output a path to use on the first
lines (eg.  ``~/.gem/ruby/2.0.0/bin/travis``)

We’ll use the Travis CI command-line client to log in (using your GitHub
password), enable the repository and encrypt our SSH key. Run the following
three commands, one at a time (they are interactive):

.. code:: console

   travis login
   travis enable
   travis encrypt-file id_rsa --add

Commit everything to GitHub:

.. code:: console

   git add .
   git commit -am "Automate builds with Travis CI"

Hopefully, Travis CI will build your site and deploy. Check the Travis CI
website or your e-mail for a notification. If there are any errors, make sure
you followed this guide to the letter.

(Revision 3, 2017-03-17: added master/src branching information, blocked non-src builds, clarified some things)

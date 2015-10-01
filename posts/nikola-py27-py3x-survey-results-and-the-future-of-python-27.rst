.. title: Environment Survey Results and the Future of Python 2.7 in Nikola
.. slug: env-survey-results-and-the-future-of-python-27
.. date: 2015-09-26 10:00:00 UTC
.. tags: python, survey, planet
.. category:
.. link:
.. description:
.. type: text
.. author: Chris Warrick

Recently, the Nikola team `asked the community`__ about the Python versions used to run Nikola. We received a total of 138 responses. The survey results are as follows:

Most users already are on Python 3
==================================

Two thirds (66%) of Nikola users are already on Python 3. Some users run both versions concurrently (for example, on different operating systems)

.. chart:: Pie
   :title: 'Python 2 and 3 users'
   :style: CleanStyle

   'Python 2 only',  46
   'Python 3 only',  73
   'Python 2 and 3', 19

A diverse selection of operating systems
========================================

The most popular operating system is Ubuntu (with 54 users), followed by Debian and Mac OS X (37 users each). There were also 27 Windows users taking part in the survey.  This was a multiple–choice question — there were 211 data points in total)

There are multiple operating system versions listed in the second (optional) question about operating systems, ranging from Debian 6 squeeze (oldstable) to the newest versions

.. chart:: Bar
   :title: 'Operating systems used by survey participants'
   :style: CleanStyle

   'Ubuntu', 54
   'Debian', 37
   'Mac OS X', 37
   'Windows', 27
   'Arch Linux', 20
   'BSD', 9
   'Linux Mint', 8
   'Fedora', 7
   'RedHat/CentOS', 3
   'openSUSE', 3
   'Gentoo', 2
   'Other', 4

Switching is not a problem for the community
============================================

Out of all the participants, only 10 (7.25%) said that they would not install a Python 3 interpreter, even if Nikola were to require one. More than 76% of our users have a Python 3 interpreter installed already.

.. chart:: Pie
   :title: 'Python 3 interpreter usage'
   :style: CleanStyle

   'Have a Python 3 interpreter', 106
   'Can install Python 3 if required', 22
   'Refuse to install Python 3', 10

Comments, concerns and suggestions
==================================

After answering the four survey questions, users could leave comments. Many of them were positive and commended the decision. Some participants even claimed that they do not like Python 2.x and it might even deter them from contributing. Many participants asked us to kill 2.7 and to go forward with Python 3.

There were, however, a few participants that had concerns about our decision. A few users cited the inability to migrate due to having existing Python 2-only software. For most people, this is not a problem — Python 2 and 3 can **coexist** on one machine, with separate packages and binaries. Those users would be just use Nikola with Python 3.x, and their legacy software with 2.7 — and it would work without any problems. The only people who could have a problem are those using 2.7–only code in plugins.

Some users also suggested bundling an interpreter with Nikola (this is done by eg. Dropbox). We believe that this is not a good thing to do. Bundling an interpreter is a lot of work, and Dropbox does this because they want to protect their code (not applicable in an open–source project) and because they have a large non-technical user base (scared by black terminal windows used by h4x0rz). However, there is a partial solution: if you prefer, you can use a `Docker image`__ that runs Nikola under Arch Linux, created by Rob Brewer (and which has been blessed by the Nikola team).

Yet another suggestion was to make Nikola available via Homebrew or MacPorts. While there is no package for Nikola available in those repositories, our `Getting Started Guide`__ recommends using Homebrew, MacPorts or Fink with virtualenv and pip on OS X, by providing install instructions for those three repositories (using Python 3). If you want a package for one of those systems, you can always contribute your own (if this is possible in those communities) — the Nikola community will be happy to use it.

There were also concerns about the ARM architecture. We have had reports of users running Nikola on ARM–based devices (including one survey participant)  — just keep in mind that it is really slow on SD cards (which is the main storage device of Raspberry Pi).

The future of Python 2.7 in Nikola
==================================

Taking the results of this survey into consideration, the Nikola developers decided that Python 2.7 support will be **dropped in Nikola v8.0.0**.  This version will be released in early 2016. Before that date, we will migrate all our remaining infrastructure to Python 3.x. The next version of Nikola, v7.7.2, will be released on 2015-10-03 and will display a warning if the user is running Python 2.7. We might keep the compatibility hacks after v8.0.0, but we will not officially support using Python 2.7 with Nikola.

Motivation (added 2015-9-27)
----------------------------

Supporting two Python versions is a lot of work.  We have to use various
compatibility hacks to make Unicode work properly, and then there are still
issues caused by the fact Python 2 was not built with Unicode in mind.  The
developers decided that it is time to let Python 2 go and thus make the
development much easier.


Switching to Python 3.x
=======================

If you are running Nikola with Python 2.7, you should switch to Python 3.x soon. Doing so is simple and is a one–time process. You should follow the `Getting Started Guide`__ for more information, or read the instructions below:

Windows
-------

1. Install Python 3.5 from the official website (`python.org`__)
2. Install virtualenv using ``py -m pip install virtualenv``
3. Create a virtualenv and activate it (for more information, read `virtualenv documentation`__)
4. Install lxml and Pillow wheels from `Christoph Gohlke’s website`__ (using ``pip install c:\paths\to\the\two\files.whl``)
5. Install Nikola using ``pip install "Nikola[extras]"``

Mac OS X
--------

Follow the “Installing on OS X” section of the `Getting Started Guide`__ to install Nikola and Python from Homebrew, MacPorts or Fink.

Linux
-----

To install Nikola using Python 3.x on Linux, you should first identify your installation method.

If you use a distribution package (eg. ``python-nikola`` from Arch Linux’s AUR, or Fedora’s packages), you should look for the Python 3 version of those packages. If those are not available, you should install Nikola manually and report a bug with your distribution.

If you installed Nikola manually, we recommend creating a virtualenv for it. Please follow the instructions in the `Getting Started Guide`__ (you might need to see the troubleshooting hints and adjust them for your OS/Python 3 package name)

(Note that Nikola requires Python 3.3 or newer; if you are running a *really* old distribution, it might not be available.)

Migrating a site
----------------

You can use your existing Nikola site with Python 3, without any special modifications to the code. However, you will likely receive this error when you run ``nikola build`` for the first time::

    doit.dependency.DatabaseException: Dependencies file in '.doit.db' seems to use an old format or is corrupted.
    To fix the issue you can just remove the database file(s) and a new one will be generated.

In case you do, you can just remove the mentioned ``.doit.db`` file and run ``nikola build`` again. Note that this will lead to rebuilding your site from scratch — but this is a **one–time process**, and the next rebuild should be an incremental one.

PS. you can also see the results on the Google Forms `results`__ summary page. If you want to do your own data analysis, we can share the raw data (.csv) — contact me (Chris Warrick) if you would like to get access.  The charts in this post were generated courtesy of `pygal`__, using the ``:chart:`` directive, which is built into Nikola.

__ https://getnikola.com/blog/nikola-environment-survey-python-273x-usage.html
__ https://github.com/rbrewer123/docker_nikola
__ https://getnikola.com/getting-started.html
__ https://getnikola.com/getting-started.html
__ https://www.python.org/
__ https://virtualenv.pypa.io/en/latest/
__ http://www.lfd.uci.edu/~gohlke/pythonlibs/
__ https://getnikola.com/getting-started.html
__ https://getnikola.com/getting-started.html
__ https://docs.google.com/forms/d/15dnvSCO0JP9IX9MvjRI3aofCQaDFcl2S0aTsApkCAbY/viewanalytics
__ http://www.pygal.org/

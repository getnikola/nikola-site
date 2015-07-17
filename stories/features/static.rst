.. title: Static
.. slug: static
.. date: 2015-07-10 15:38:32 UTC
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Most "modern" websites are *dynamic* in the sense that the contents of the site
live in a database, and are converted into presentation-ready HTML only when a
user wants to see the page. That's great. However, it presents some minor issues
that static site generators try to solve.

In a static site, the whole site, every page, *everything*, is created before
the first user even sees it and uploaded to the server as a simple folder full
of HTML files (and images, CSS, etc).

So, let's see some reasons for using static sites:

Security
    Dynamic sites are prone to experience security issues. The solution for that
    is constant vigilance, keeping the software behind the site updated, and
    plain old good luck. The stack of software used to provide a static site,
    like those Nikola generates, is much smaller (Just a web server).

    A smaller software stack implies less security risk.

Obsolescense
    If you create a site using (for example) WordPress, what happens when WordPress
    releases a new version? You have to update your WordPress. That is not optional,
    because of security and support issues. If I release a new version of Nikola, and
    you don't update, *nothing* happens. You can continue to use the version you
    have now forever, no problems.

    Also, in the longer term, the very foundations of dynamic sites shift. Can you
    still deploy a blog software based on Django 0.96? What happens when your
    host stops supporting the php version you rely on? And so on.

    You may say those are long term issues, or that they won't matter for years. Well,
    I believe things should work forever, or as close to it as we can make them.
    Nikola's static output and its input files will work as long as you can install
    a Python 2.7/3.3 or newer under Linux, Windows, or OS X and can find a server
    that sends files over HTTP. That's probably 10 or 15 years at least.

    Also, static sites are easily handled by the Internet Archive.

Cost and Performance
    On dynamic sites, every time a reader wants a page, a whole lot of database
    queries are made. Then a whole pile of code chews that data, and HTML is
    produced, which is sent to the user. All that requires CPU and memory.

    On a static site, the highly optimized HTTP server reads the file from disk
    (or, if it's a popular file, from disk cache), and sends it to the user. You could
    probably serve a bazillion (technical term) pageviews from a phone using
    static sites.

Lock-in
    On server-side blog platforms, sometimes you can't export your own data, or
    it's in strange formats you can't use in other services. I have switched
    blogging platforms from Advogato to PyCs to two homebrew systems, to Nikola,
    and have never lost a file, a URL, or a comment. That's because I have *always*
    had my own data in a format of my choice.

    With Nikola, you own your files, and you can do anything with them.

.. title: Template variables
.. slug: template-variables
.. date: 2017-04-13 12:00:00
.. author: The Nikola Team

:Version: 8.3.1
:Author: Chris Warrick <chris@getnikola.com>

Variables available in templates are listed below.

* This list is maintained by humans, so it may not always be perfect.
* Variables whose types are marked with ``?`` may not always be available or may be None in some cases.
* Templates usually do not have access to the original TranslatableSetting
  variables, only to the current locale version (except ``NAVIGATION_LINKS``).
* For function and setting documentation, please consult `code documentation
  <https://docs.getnikola.com/en/latest/modules/>`_ and `default configuration
  <https://getnikola.com/conf.html>`_ respectively.
* Templates often create their own functions (macros), and import macros from
  other templates. Those macros are not listed here.
* This list has a partial documentation of post objects, but no other objects. For full docs, please consult
  the code, or auto-generated code docs on `ReadTheDocs <https://nikola.readthedocs.io/>`_.

Variables and functions come from three places:

* the global context
* the local context of a page
* the templates themselves and the templates they import

.. class:: alert alert-primary
.. contents::

Global variables
----------------

Some variables on the global variables list may be None (the ``?`` symbol is not used).

.. class:: table table-bordered table-striped

==================================  ==================================  ================================================================================
Name                                Type                                Description
==================================  ==================================  ================================================================================
``_link``                           function                            ``Nikola.link`` function
``abs_link``                        function                            ``Nikola.abs_link`` function
``atom_path``                       TranslatableSetting[str]            ``ATOM_PATH`` setting
``author_pages_generated``          bool                                False
``blog_author``                     TranslatableSetting[str]            ``BLOG_AUTHOR`` setting
``blog_email``                      str                                 ``BLOG_EMAIL`` setting
``blog_description``                TranslatableSetting[str]            ``BLOG_DESCRIPTION`` setting
``blog_title``                      TranslatableSetting[str]            ``BLOG_TITLE`` setting
``blog_url``                        str                                 ``SITE_URL`` setting
``body_end``                        TranslatableSetting[str]            ``BODY_END`` setting
``colorize_str_from_base_color``    function                            ``utils.colorize_str_from_base_color`` function
``color_hsl_adjust_hex``            function                            ``utils.color_hsl_adjust_hex`` function
``comment_system_id``               str                                 ``COMMENT_SYSTEM_ID`` setting
``comment_system``                  str                                 ``COMMENT_SYSTEM`` setting
``content_footer``                  TranslatableSetting[str]            ``CONTENT_FOOTER`` setting
``data``                            dict                                data files (from the ``data/`` directory)
``date_fanciness``                  int                                 ``DATE_FANCINESS`` setting
``date_format``                     TranslatableSetting[str]            ``DATE_FORMAT`` setting
``exists``                          function                            ``Nikola.file_exists`` function
``extra_head_data``                 TranslatableSetting[str]            ``EXTRA_HEAD_DATA`` setting
``favicons``                        tuple                               ``FAVICONS`` setting
``front_index_header``              TranslatableSetting[str]            ``FRONT_INDEX_HEADER`` setting
``generate_atom``                   bool                                ``GENERATE_ATOM`` setting
``generate_rss``                    bool                                ``GENERATE_RSS`` setting
``global_data``                     dict                                alias for ``data``
``has_custom_css``                  bool                                True if custom.css exists
``hidden_authors``                  list[str]                           ``HIDDEN_AUTHORS`` setting
``hidden_categories``               list[str]                           ``HIDDEN_CATEGORIES`` setting
``hidden_tags``                     list[str]                           ``HIDDEN_TAGS`` setting
``hide_sourcelink``                 bool                                ``SHOW_SOURCELINK`` setting, negated
``index_display_post_count``        int                                 ``INDEX_DISPLAY_POST_COUNT`` setting
``index_file``                      str                                 ``INDEX_FILE`` setting
``js_date_format``                  TranslatableSetting[str]            ``MOMENTJS_DATE_FORMAT`` setting, JSONified
``katex_auto_render``               str                                 ``KATEX_AUTO_RENDER`` setting
``license``                         TranslatableSetting[str]            ``LICENSE`` setting
``logo_url``                        str                                 ``LOGO_URL`` setting
``luxon_date_format``               TranslatableSetting[str]            ``LUXON_DATE_FORMAT`` setting, JSONified
``mathjax_config``                  str                                 ``MATHJAX_CONFIG`` setting
``messages``                        dict[dict[str, str]]                translated messages (``{language: {english: translated}}``)
``meta_generator_tag``              bool                                ``META_GENERATOR_TAG`` setting
``momentjs_locales``                defaultdict[str, str]               dictionary of available Moment.js locales
``multiple_authors_per_post``       bool                                ``MULTIPLE_AUTHORS_PER_POST`` setting
``navigation_links``                TranslatableSetting                 ``NAVIGATION_LINKS`` setting
``navigation_alt_links``            TranslatableSetting                 ``NAVIGATION_ALT_LINKS`` setting
``needs_ipython_css``               bool                                whether or not Jupyter CSS is needed by this site
``rel_link``                        function                            ``Nikola.rel_link`` function
``rss_link``                        str                                 ``RSS_LINK`` setting
``search_form``                     TranslatableSetting[str]            ``SEARCH_FORM`` setting
``set_locale``                      function                            ``LocaleBorg.set_locale`` function (or None if not available)
``show_blog_title``                 bool                                ``SHOW_BLOG_TITLE`` setting
``show_sourcelink``                 bool                                ``SHOW_SOURCELINK`` setting
``site_has_comments``               bool                                whether or not a comment system is configured
``social_buttons_code``             TranslatableSetting[str]            ``SOCIAL_BUTTONS_CODE`` setting
``sort_posts``                      function                            ``utils.sort_posts`` function
``smartjoin``                       function                            ``utils.smartjoin`` function
``colorize_str``                    function                            ``utils.colorize_str`` function
``template_hooks``                  dict[str, TemplateHookRegistry]     Template hooks registered by plugins
``theme_color``                     str                                 ``THEME_COLOR`` setting
``theme_config``                    dict                                ``THEME_CONFIG`` setting
``timezone``                        tzinfo                              Timezone object (represents the configured timezone)
``translations``                    dict[str, str]                      ``TRANSLATIONS`` setting
``twitter_card``                    dict                                ``TWITTER_CARD`` setting, defaults to an empty dictionary
``url_replacer``                    function                            ``Nikola.url_replacer`` function
``url_type``                        str                                 ``URL_TYPE`` setting
``use_bundles``                     bool                                ``USE_BUNDLES`` setting
``use_cdn``                         bool                                ``USE_CDN`` setting
``use_katex``                       bool                                ``USE_KATEX`` setting
``subtheme``                        str?                                ``THEME_REVEAL_CONFIG_SUBTHEME`` setting (only if set — deprecated)
``transition``                      str?                                ``THEME_REVEAL_CONFIG_TRANSITION`` setting (only if set — deprecated)
==================================  ==================================  ================================================================================

Per-page local variables
------------------------

Those variables are available on all pages, but their contents are dependent on page contents.

.. class:: table table-bordered table-striped

==================  ==========  ===============================================================
Name                Type        Description
==================  ==========  ===============================================================
``description``     str         Description of the page
``is_rtl``          bool        Whether or not the language is left-to-right
``lang``            str         Current language
``pagekind``        list[str]   List of strings that identify the type of this page `(docs)`__
``title``           str         Title of the page (taken from post, config, etc.)
``formatmsg``       function    Wrapper over ``%`` string formatting
``striphtml``       function    Strips HTML tags (Mako only)
``crumbs``          list        Breadcrumbs for this page
==================  ==========  ===============================================================

__ https://getnikola.com/theming.html#identifying-and-customizing-different-kinds-of-pages-with-a-shared-template

Variables available in post pages (``post.tmpl``, ``page.tmpl`` etc.)
---------------------------------------------------------------------

.. class:: table table-bordered table-striped

======================  ==========  ========================================================
Name                    Type        Description
======================  ==========  ========================================================
``post``                Post        The post object
``permalink``           str         Permanent link to the post
``enable_comments``     bool        True for posts, ``COMMENTS_IN_PAGES`` setting for pages
======================  ==========  ========================================================

Variables available in post lists
---------------------------------

.. class:: table table-bordered table-striped

==============  =============  ==============================================
Name            Type           Description
==============  =============  ==============================================
``posts``       list[Post]     List of post objects that appear in this list
``prevlink``    str            Link to previous page
``nextlink``    str            Link to next page
==============  =============  ==============================================


Variables available in indexes
------------------------------

.. class:: table table-bordered table-striped

==============================  ==============  ===============================================================================
Name                            Type            Description
==============================  ==============  ===============================================================================
``posts``                       list[Post]      List of post objects that appear in this list
``index_teasers``               bool            ``INDEX_TEASERS`` setting
``show_index_page_navigation``  bool            ``SHOW_INDEX_PAGE_NAVIGATION`` setting
``current_page``                int             Number of current page
``page_links``                  list[str]       Links to different pages
``prevlink``                    str             Link to previous page
``nextlink``                    str             Link to next page
``prevfeedlink``                str             Link to previous page as an Atom feed
``nextfeedlink``                str             Link to next page as an Atom feed
``prev_next_links_reversed``    bool            Whether or not previous and next links should be reversed (``INDEXES_STATIC``)
``is_frontmost_index``          bool            Whether or not this is the front-most index (page 0)
==============================  ==============  ===============================================================================

Variables available in taxonomies
---------------------------------

Variable names enclosed in ``{}`` are dependent on the taxonomy.

.. class:: table table-bordered table-striped

======================  ==========================================  ===================
Taxonomy                Variable                                    Value
======================  ==========================================  ===================
``archive``             ``overview_page_variable_name``             ``archive``
``author``              ``overview_page_variable_name``             ``authors``
``category``            ``overview_page_variable_name``             ``categories``
``category``            ``overview_page_items_variable_name``       ``cat_items``
``category``            ``overview_page_hierarchy_variable_name``   ``cat_hierarchy``
``index``               ``overview_page_variable_name``             unavailable (None)
``page_index_folder``   ``overview_page_variable_name``             ``page_folder``
``tag``                 ``overview_page_variable_name``             ``tags``
``tag``                 ``overview_page_items_variable_name``       ``items``
======================  ==========================================  ===================

Templates and settings used by taxonomies
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. class:: table table-bordered table-striped

======================  ==================  ==================================  ======================================  ==============================================  ======================================  ==============================  ==============================
Taxonomy                Has hierarchy       List (one classification) template  Index (one classification) template     Overview (list of classifications) template     Subcategories list template             List is an index                Show as list of subcategories
======================  ==================  ==================================  ======================================  ==============================================  ======================================  ==============================  ==============================
(default settings)      no                  tagindex.tmpl                       tagindex.tmpl                           list.tmpl                                       taxonomy_list.tmpl (does not exist)     no                              no
``archive``             yes (0-3 levels)    list_post.tmpl                      archiveindex.tmpl                       list.tmpl                                       list.tmpl                               ``ARCHIVES_ARE_INDEXES``        ``not CREATE_FULL_ARCHIVES``
``author``              no                  author.tmpl                         authorindex.tmpl                        authors.tmpl                                    n/a                                     ``AUTHOR_PAGES_ARE_INDEXES``    no
``category``            yes                 tag.tmpl                            tagindex.tmpl                           tags.tmpl (with tags)                           n/a                                     ``CATEGORY_PAGES_ARE_INDEXES``  n/a
``index``               no                  n/a                                 index.tmpl                              n/a                                             n/a                                     yes                             no
``page_index_folder``   yes                 list.tmpl                           n/a                                     n/a                                             n/a                                     no                              no
``tag``                 no                  tag.tmpl                            tagindex.tmpl                           tags.tmpl (with categories)                     n/a                                     ``TAG_PAGES_ARE_INDEXES``       no
======================  ==================  ==================================  ======================================  ==============================================  ======================================  ==============================  ==============================

Classification overviews
~~~~~~~~~~~~~~~~~~~~~~~~

Hierarchy-related variables are available if and only if ``has_hierarchy`` is True.

.. class:: table table-bordered table-striped

==================================================================  ======  ==============================================================================================================================================================================
Name                                                                Type    Description
==================================================================  ======  ==============================================================================================================================================================================
``{overview_page_variable_name}``                                   str     List of classifications
``{overview_page_items_variable_name}``                             list    List of items *(name, link)*
``{overview_page_items_variable_name + "_with_postcount"}``         list    List of items *(name, link, number of posts)*
``{overview_page_hierarchy_variable_name}``                         list?   List of hierarchies *(name, full name, path, link, indent levels, indent to change before, indent to change after)*
``{overview_page_hierarchy_variable_name + "_with_postcount"}``     list?   List of hierarchies, with added counts *(name, full name, path, link, indent levels, indent to change before, indent to change after, number of children, number of posts)*
``has_hierarchy``                                                   bool    Value of ``has_hierarchy`` for the taxonomy
``permalink``                                                       str     Permanent link to page
==================================================================  ======  ==============================================================================================================================================================================

Classification pages (lists)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. class:: table table-bordered table-striped

===================  ==============  =============================================================
Name                 Type            Description
===================  ==============  =============================================================
``kind``             str             The classification name
``items``            list?           List of items for ``list.tmpl`` *(title, permalink, None)*
``posts``            list[Post]?     List of items for other templates
``permalink``        str             Permanent link to page
``other_languages``  list[tuple]     List of triples ``(other_lang, other_classification, title)``
===================  ==============  =============================================================

Index-style classification pages have ``kind`` in addition to the usual index variables.

Subclassification page
~~~~~~~~~~~~~~~~~~~~~~

.. class:: table table-bordered table-striped

===================  ===========  =============================================================
Name                 Type         Description
===================  ===========  =============================================================
``items``            list?        List of items
``permalink``        str          Permanent link to page
``other_languages``  list[tuple]  List of triples ``(other_lang, other_classification, title)``
===================  ===========  =============================================================

Hierarchical lists
~~~~~~~~~~~~~~~~~~

The indenting information can be used to render the items as a tree. The values have the following meanings:

 * ``indent levels`` is a list of pairs ``(current_i, count_i)`` giving the current position (``0``, ..., ``count_i-1``) and maximum (``count_i``) in the hierarchy level ``i``;
 * ``indent to change before`` is the difference of hierarchy levels between the previous and the current item; positive values indicate that the current item is indented further in and can be used to open HTML tags before the item;
 * ``indent to change after`` is the difference of hierarchy levels between the current and the next item; negative values indicate that the current item is indented further in and can be used to close HTML tags after the item.

Example:

.. code:: text

   +--- levels:[(0,3)], before:1, after:0
   +-+- levels:[(1,3)], before:0, after:1
   | +--- levels:[(1,3), (0,2)], before:1, after:0
   | +-+- levels:[(1,3), (1,2)], before:0, after:1
   |   +--- levels:[(1,3), (1,2), (0, 1)], before:1, after:-2
   +-+- levels:[(2,3)], before:-2, after:1
     +- levels:[(2,3), (0,1)], before:1, after:-2

See ``tags.tmpl`` in the base themes for examples on how to render a tree as nested unordered lists in HTML.

Variables available in archives
-------------------------------

The archive navigation variables are available only if ``create_archive_navigation`` is True.

.. class:: table table-bordered table-striped

==============================  ==============  ========================================================================
Name                            Type            Description
==============================  ==============  ========================================================================
``kind``                        str             Always ``"archive"``
``archive_name``                str?            Name of the archive (only if using indexes)
``create_archive_navigation``   bool            ``CREATE_ARCHIVE_NAVIGATION`` setting
``has_archive_navigation``      bool            Whether or not archive navigation is available
``up_archive``                  str?            Link to the archive one level up
``up_archive_name``             str?            Name of the archive one level up
``previous_archive``            str?            Link to the previous archive
``previous_archive_name``       str?            Name of the previous archive
``next_archive``                str?            Link to the next archive
``next_archive_name``           str?            Name of the next archive
``archive_nodelevel``           int?            Level of the archive
``other_languages``             list            List of tuples ``(lang, path, name)`` of same archive in other languages
==============================  ==============  ========================================================================


Variables available in author pages
-----------------------------------

.. class:: table table-bordered table-striped

===================  ===========  =========================================================================
Name                 Type         Description
===================  ===========  =========================================================================
``kind``             str          Always ``"author"``
``author``           str          Author name
``rss_link``         str          Link to RSS (HTML fragment)
``other_languages``  list[tuple]  List of tuples ``(lang, author, name)`` of same author in other languages
===================  ===========  =========================================================================


Variables available in category pages
-------------------------------------

.. class:: table table-bordered table-striped

===================  ===========  =============================================================================
Name                 Type         Description
===================  ===========  =============================================================================
``kind``             str          Always ``"category"``
``category``         str          Category name
``category_path``    list[str]    Category hierarchy
``rss_link``         str?         Link to RSS (HTML fragment, only if using indexes)
``subcategories``    list         List of subcategories (contains *name, link* tuples)
``tag``              str          Friendly category name
``other_languages``  list[tuple]  List of tuples ``(lang, category, name)`` of same category in other languages
===================  ===========  =============================================================================

Variables available in galleries
--------------------------------

.. class:: table table-bordered table-striped

======================  ==========  ===============================================================================
Name                    Type        Description
======================  ==========  ===============================================================================
``crumbs``              list        Breadcrumbs for this page
``enable_comments``     bool        Whether or not comments are enabled in galleries
``folders``             list        List of folders (contains *path, title* tuples)
``permalink``           str         Permanent link to this page
``photo_array``         list        Photo array (contains dicts with image data: *url, url_thumb, title, size{w, h}*)
``photo_array_json``    str         Photo array in JSON format
``post``                Post?       The Post object for this gallery
``thumbnail_size``      int         ``THUMBNAIL_SIZE`` setting
======================  ==========  ===============================================================================


Variables available in listings
-------------------------------

.. class:: table table-bordered table-striped

==================  ==========  ========================================
Name                Type        Description
==================  ==========  ========================================
``code``            str         Highlighted source code (HTML fragment)
``crumbs``          list        Breadcrumbs for this page
``folders``         list[str]   List of subfolders
``files``           list[str]   List of files in the folder
``source_link``     str         Link to the source file
==================  ==========  ========================================

Variables available in tag pages
--------------------------------

.. class:: table table-bordered table-striped

===================  ===========  ===================================================================
Name                 Type         Description
===================  ===========  ===================================================================
``kind``             str          Always ``"tag"``
``tag``              str          Tag name
``other_languages``  list[tuple]  List of tuples ``(lang, tag, name)`` of same tag in other languages
===================  ===========  ===================================================================

Variables available in the “Tags and categories” page (``tags.tmpl``)
---------------------------------------------------------------------

.. class:: table table-bordered table-striped

=========================  ======  ===========================================================================================================
Name                       Type    Description
=========================  ======  ===========================================================================================================
``items``                  list    Tags *(name, link)*
``cat_items``              list    Categories *(name, full name, path, link, indent levels, indent to change before, indent to change after)*
``category_titles``        dict    ``CATEGORY_TITLES`` setting (dict for the current language only)
``category_descriptions``  dict    ``CATEGORY_DESCRIPTIONS`` setting (dict for the current language only)
``tag_titles``             dict    ``TAG_TITLES`` setting (dict for the current language only)
``tag_descriptions``       dict    ``TAG_DESCRIPTIONS`` setting (dict for the current language only)
=========================  ======  ===========================================================================================================

For more details about hierarchies, see `Hierarchical lists`_

Variables available in shortcodes
---------------------------------

*The global context is available in templated shortcodes.*

.. class:: table table-bordered table-striped

==================  ==========  ===========================================================================
Name                Type        Description
==================  ==========  ===========================================================================
``lang``            str         Current language
``_args``           list[str]   Arguments given to the shortcode
``data``            str         Shortcode contents
``post``            Post        Post object (if available)
``filename``        str?        file name, if ``shortcode_function.nikola_shortcode_pass_filename = True``
==================  ==========  ===========================================================================

Variables available in post lists
---------------------------------

*The global context is NOT available in post lists.*

.. class:: table table-bordered table-striped

==================  ==========  =====================================
Name                Type        Description
==================  ==========  =====================================
``posts``           list[Post]  Posts that are on the list
``lang``            str         Current language
``date_format``     str         The date format for current language
``post_list_id``    str         GUID of post list
``messages``        dict        The messages dictionary
``_link``           function    ``Nikola.link`` function
==================  ==========  =====================================

Post object attributes
----------------------

*Usable anywhere post objects are accessible.*

This list only includes variables that make sense for templates. Some function signatures have been shortened to save space, ``?`` means the argument has default value.

More docs: `nikola.post.Post on ReadTheDocs <https://nikola.readthedocs.io/en/latest/nikola.html#nikola.post.Post>`_. Check out the source of the Post class as well.

===================================================================  ==========  =============================================================
Name                                                                 Type        Description
===================================================================  ==========  =============================================================
``alltags``                                                          list[str]   All tags for the post
``author(lang=None)``                                                str         Localized author or ``BLOG_AUTHOR``
``base_path``                                                        str         ``cache`` path with local ``os.sep``
``category_from_destpath``                                           bool        If category was set by ``CATEGORY_DESTPATH_AS_DEFAULT``
``data(key, lang=None)``                                             ?           Access to post data
``date``                                                             datetime    Date of post (from meta)
``description(key, lang=None)``                                      str         Description of post (from meta)
``destination_path(lang?, extension?, sep?)``                        str         Destination path of post
``formatted_date(date_format, date=None)``                           str         Format a date (default: post date)
``formatted_updated(date_format)``                                   str         Format the last update date
``guid(lang=None)``                                                  str         GUID of post (used for feeds)
``has_math``                                                         bool        If the post has math
``has_pretty_url(lang)``                                             bool        If the post has a pretty URL
``is_draft``                                                         bool        If the post is a draft
``is_post``                                                          bool        If the post is not a page
``is_private``                                                       bool        If the post is private
``is_translation_available(lang)``                                   bool        If the post is available in (translated to) a given language
``is_two_file``                                                      bool        If the post uses two-file metadata
``meta(key, lang=None)``                                             ?           Metadata of the post (assumes current language)
``next_post``                                                        Post        Next post in the order
``paragraph_count``                                                  int         Paragraph count for a post
``permalink(lang?, absolute?, extension?, query?)``                  str         Permanent link for a post
``post_name``                                                        str         Source path, without extension
``post_status``                                                      str         Post status meta field (published, featured, private, draft)
``prev_post``                                                        Post        Previous post in the order
``previewimage``                                                     str         Preview image of the post
``publish_later``                                                    bool        True if the post is not yet published (due to date)
``reading_time``                                                     int         Approximate reading time in minutes (220 wpm)
``remaining_paragraph_count``                                        int         Paragraph count after the teaser
``remaining_reading_time``                                           int         Reading time after the teaser
``source_link``                                                      str         Absolute link to the post's source
``tags``                                                             list[str]   Tags for the current language
``tags_for_language(lang)``                                          list[str]   Tags for a given language
``text(lang?, teaser_only?, strip_html?, show_read_more_link?, …)``  str         The text of a post
``title(lang=None)``                                                 str         Localized title of post
``translated_to``                                                    list[str]   List of languages of post
``updated``                                                          datetime    Date of last update (from meta)
``use_in_feeds``                                                     bool        If this post should be displayed in feeds
===================================================================  ==========  =============================================================

.. vim: nowrap textwidth=0

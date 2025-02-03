===========
IIIF Search
===========

-----------
Description
-----------

Currently, Fedora is only used images and textual works where we don't care about search within text. When we care about
search within text, we use either `OpenOni <https://github.com/open-oni/open-oni>`_ or
`InternetArchive Bookreader <https://github.com/TAMULib/tl_docker/tree/master/apache_php8-bookreader>`_ to deliver collections.
This is problematic for a few reasons:

1. you can't reuse one of these works in an exhibit
2. we aren't managing these files or works in our repository
3. the works aren't represented by a IIIF manifest to encourage remix or reuse of the work
4. we have to maintain those other products
5. some of our collections don't fit nicely in those other applications

We could eliminate the need for these repositories and bring in the same search behavior to Fedora by adopting
`IIIF Content Search <https://iiif.io/api/search/2.0/>`_.

-------
Request
-------

* A IIIF Content Search is created that allows structured text about an image to be indexed in Solr and available via a IIIF Content Search Service.

-------------------
Acceptance Criteria
-------------------

* A IIIF Content Search Service is adopted or created.
* Structured Text is storeable in Fedora and indexed in Solr and fed to the IIIF content search service.

-----------------
Notes or Examples
-----------------

There are several IIIF Content Search Services in use.  Blacklight has one that works out of the box. IIIF Simple Annotation
Server also has its own.  Archipelago has its own modules that do this.

While we probably don't want to adopt any of these, a `popular SOLR plugin <https://github.com/dbmdz/solr-ocrhighlighting/>`_
is used by most of these to simplify some of the most complex parts.


----------------
Related Requests
----------------


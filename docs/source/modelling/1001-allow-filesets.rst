=======================
Allow Filesets in Works
=======================

-----------
Description
-----------

Often, a work may have a group of interconnected files that must be organized together in order to be understood or reused.
For instance, an image of a page of a book may be represented as a JP2, a text file that includes all OCR text on the page,
and structured text such an HOCR or ALTO XML file. For this specific use case, the PCDM Works ontology defines the
:code:`pcdmworks:FileSet`, a subclass of :code:`pcdm:Object` that is used to represent a group of related Files,
typically a single source File and any of its derivatives.

-------
Request
-------

As a librarian, I need a way to manage files that are related to one another in Fedora so that they can be reused and
interoperable in external systems while also being understood according to adopted open standards.

-------------------
Acceptance Criteria
-------------------

* The tools used to deposit and store data in Fedora offer a way to establish a fileset and its parts.
* The Portland Common Data Model Works ontology is leveraged.

-----------------
Notes or Examples
-----------------

An example graph might look like this:

.. code-block:: ttl

    @prefix ex: <http://example.org/> .
    @prefix fedora: <http://fedora.info/definitions/v4/repository#> .
    @prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
    @prefix pcdm: <http://pcdm.org/models#> .
    @prefix pcdmworks: <http://pcdm.org/works#> .
    @prefix pcdmuse: <http://pcdm.org/use#> .
    @prefix pcdmff: <http://pcdm.org/file-format-types#> .

    ex:PageOneOfABook a pcdmworks:Fileset ;
        rdfs:label "Example Book: Page 1" ;
        pcdm:memberOf ex:Book ;
        pcdm:hasFile ex:Image, ex:HOCR, ex:OCR .

    ex:Image a pcdmuse:ServiceFile, pcdmff:Image ;
        pcdm:fileOf ex:PageOneOfABook ;
        fedora:hasBinary <https://path/to/image_0001.jp2> .

    ex:HOCR a pcdmff:HTML ;
        pcdm:fileOf ex:PageOneOfABook ;
        fedora:hasBinary <https://path/to/image_0001.html> .

    ex:OCR a pcdmuse:ExtractedText ;
        pcdm:fileOf ex:PageOneOfABook ;
        fedora:hasBinary <https://path/to/image_0001.txt> .

----------------
Related Requests
----------------


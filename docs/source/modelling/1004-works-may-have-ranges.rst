=====================
Works May Have Ranges
=====================

-----------
Description
-----------

Some works such as books, compound objects, or complex audio visual works may have a hierarchy that describes the
various sections and subsections of an item. By creating a Range to represent each section and subsection, a IIIF viewer
can leverage this data and provide users a way to navigate across a work using each these resources.

The `PCDM Works Extension <https://pcdm.org/2021/04/09/works>`_ defines multiple two classes for modelling this type of
data: :code:`pcdmworks:TopRange` and :code:`pcdmworks:Range`. These classes were informed by the IIIF Presentation API.
Prior to version 3 of the API specification, the top most Range required a viewingHint="top" property, and the
:code:`pcdmworks:TopRange` class provided a way to distinguish between the two. As of version 3.0 of the API, this
requirement is no longer needed and thus I only think having this is required if it eases things for a developer. A
:code:`pcdmworks:TopRange` might be useful for storing ranges.

-------
Request
-------

* :code:`pcdmworks:Ranges` are modelled in Fedora and point at member :code:`pcdmworks:FileSets`.

-------------------
Acceptance Criteria
-------------------

* A Fedora work can have :code:`pcdmworks:Ranges` and point at member :code:`pcdmworks:FileSets`.
* Decisions are made about whether a range must point at a :code:`pcdmworks:FileSet` or a :code:`pcdm:File`.
* Decisions are made about the container for a set of :code:`pcdmworks:Ranges`.

-----------------
Notes or Examples
-----------------

A range may look like this:

.. code-block:: turtle

    @prefix ex: <http://example.org/> .
    @prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
    @prefix pcdm: <http://pcdm.org/models#> .
    @prefix pcdmworks: <http://pcdm.org/works#> .

    ex:Range a pcdmworks:Range ;
        rdfs:label "An Example Top Level Range" ;
        pcdm:memberOf ex:Work ;
        pcdm:hasMember ex:FileSet .

----------------
Related Requests
----------------

* :doc:`extras/2001_iiif_presentation_3`

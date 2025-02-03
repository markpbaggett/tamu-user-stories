===================================
Collections can Contain Collections
===================================

-----------
Description
-----------

A :code:`pcdm:Collection` should be able to contain: other collections, works, or both. This will ensure that our IIIF
presentation service can accurately generate a IIIF Presentation Collection resource that references its manifests and
collections.

-------
Request
-------

I want to be able to model a collection in another collection in the repository.

-------------------
Acceptance Criteria
-------------------

* I am able to model a collection in another collection and have it interoperable with other services.

-----------------
Notes or Examples
-----------------

A :code:`pcdm:Collection` is not a :code:`pcdm:Object`. It is an instance of :code:`ore:Aggregation` and might look
something like this:

.. code-block:: turtle

    @prefix ex: <http://example.org/> .
    @prefix pcdm: <http://pcdm.org/models#> .
    @prefix dc: <http://purl.org/dc/elements/1.1/> .

    ex:Collection a pcdm:Collection ;
        dc:title "My Image Collection" ;
        pcdm:hasMember ex:ImageOne, ex:ImageTwo, ex:ImageThree, ex:ImageFour .

A Collection MUST:

* be an instance of :code:`pcdm:Collection` via the :code:`rdf:type` property.
* be related to parent Collections or child works via :code:`pcdm:memberOf` or :code:`pcdm:hasMember` properties.
* have mandatory descriptive elements as stated by Metadata Guidelines for Digital Resources at Texas A&M University Libraries

A Collection MAY:

* have other descriptive metadata properties.
* have many objects or filesets.
* have proxies if the works in the collection require order.

A Collection MUST NOT:

* contain child files directly.

More information may be found in `Colleciton <https://tamu-cookbook.readthedocs.io/en/latest/components/0005_collection.html>`_

----------------
Related Requests
----------------

* :doc:`extras/2001_iiif_presentation_3`
==========================
Not All Files are a Canvas
==========================

-----------
Description
-----------

Works may have be files that serve other purposes than being painted and tiled in a viewer. They may be for download, to
supplement the file as a transcript, or to supplement a file as structured text (ALTO / HOCR). They may also may be
included so that they can be found and downloaded from a IIIF Mirador viewer through a rendering property.

-------
Request
-------

I want to be able to state what a file is and have it be treated accordingly.

-------------------
Acceptance Criteria
-------------------

* The ability to state whether a file is a canvas that should painted in a viewer and store that in Fedora.
* The ability to state whether a file supplements another file and should supplement a canvas and if so how and store that in Fedora.
* The ability to state whether a file is not related to a canvas but instead should be shared via a `rendering` or `seeAlso` property in a IIIF manifest and store that in Fedora.

-----------------
Notes or Examples
-----------------

Example File types were defined in the Fall in `File: Subtypes and Use Cases <https://tamu-cookbook.readthedocs.io/en/latest/components/0000_file_types.html#>`_.

The IIIF Presentation API describes the `rendering property <https://iiif.io/api/presentation/3.0/#rendering>`_ as an
alternative, non-IIIF representation of the resource. This property would be used for a PDF representation of a book or
perhaps a Geospatial dataset related to an image file.

The Presentation API defines the `seeAlso property <https://iiif.io/api/presentation/3.0/#seealso>`_ as a machine readable
resource that is related to the current resource. This could be used for a variety of use cases including additional metadata
formats beyond what exists in the RDF properties on a work.

Examples of how file type might be understood is via the `rdf:type` of a file in Fedora is described in detail at
`File: Subtypes and Use Cases <https://tamu-cookbook.readthedocs.io/en/latest/components/0000_file_types.html#>`_. An
example of a Geospatial Dataset might be something like:

.. code-block:: turtle

    @prefix ex: <http://example.org/> .
    @prefix fedora: <http://fedora.info/definitions/v4/repository#> .
    @prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
    @prefix pcdm: <http://pcdm.org/models#> .
    @prefix pcdmff: <http://pcdm.org/file-format-types#> .
    @prefix pcdmuse: <http://pcdm.org/use#> .
    @prefix nepomuk: <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#> .
    @prefix exif: <http://www.w3.org/2003/12/exif/ns#> .
    @prefix ebucore: <http://www.ebu.ch/metadata/ontologies/ebucore/ebucore#> .
    @prefix premis: <http://www.loc.gov/premis/rdf/v1#> .

    ex:Dataset a pcdmff:Dataset;
        pcdm:fileOf ex:ImageWork ;
        fedora:hasBinary <https://path/to/preservation%20file.zip> .
        ebucore:fileSize "17765536"^^<http://www.w3.org/2001/XMLSchema#string> ;
        premis:hasSize "17765536"^^<http://www.w3.org/2001/XMLSchema#long> ;
        ebucore:hasMimeType "application/zip"^^<http://www.w3.org/2001/XMLSchema#string> ;
        nepomuk:hashValue "99d14ee8c28517e10c637e0e0a675b94"^^<http://www.w3.org/2001/XMLSchema#string> ;
        ebucore:filename "georeferenced_CML_London_3736648_Carys.zip"^^<http://www.w3.org/2001/XMLSchema#string> .

Examples of how these might be cross-walked to IIIF Presentation can be seen below:

* `Cary's survey of the high roads from London to Hampton Court . . . <https://samvera-labs.github.io/clover-iiif/docs/viewer/demo?iiif-content=https%3A%2F%2Fmarkpbaggett.github.io%2Fstatic_iiif%2Fmanifests%2Fbrainstorming%2Flondon_maps_11.json>`_ from the London Maps collection with a Geospatial Dataset via the rendering prop in Clover.
* `Cary's survey of the high roads from London to Hampton Court . . . <https://projectmirador.org/embed/?iiif-content=https://markpbaggett.github.io/static_iiif/manifests/brainstorming/london_maps_11.json>`_ from the London Maps collection with a Geospatial Dataset via the rendering prop in Mirador.
* `Cary's survey of the high roads from London to Hampton Court . . . <https://theseus-viewer.netlify.app/?iiif-content=https://markpbaggett.github.io/static_iiif/manifests/brainstorming/london_maps_11.json>`_ from the London Maps collection with a Geospatial Dataset via the rendering prop in Theseus.

----------------
Related Requests
----------------


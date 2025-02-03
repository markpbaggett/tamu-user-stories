=================
Add a Triplestore
=================

-----------
Description
-----------

In order to simplify the number of requests needed to find Fedora content, I'd love to have a populated
triple store.  The triple store could also serve other services and solve complex requests in a much faster way.

-------
Request
-------

Install Blazegraph, JENA Fuskei, or something else, and sync it with Fedora

-------------------
Acceptance Criteria
-------------------

* Triplestore is installed.
* Data is populated from Fedora and kept in sync according to Fedora docs.

-----------------
Notes or Examples
-----------------

In case it's useful, a triple store could help do things like:

Find all files in the repository that are JP2s:

.. code-block:: sparql

    PREFIX ebucore: <http://www.ebu.ch/metadata/ontologies/ebucore/ebucore#>

    SELECT ?jp2 WHERE {
        ?jp2 ebucore:hasMimeType "image/jp2" .
    }

Find any works that have an attached HOCR file.

.. code-block:: sparql

    PREFIX ex: <http://example.org/>
    PREFIX fedora: <http://fedora.info/definitions/v4/repository#>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX pcdm: <http://pcdm.org/models#>
    PREFIX pcdmworks: <http://pcdm.org/works#>
    PREFIX pcdmuse: <http://pcdm.org/use#>
    PREFIX pcdmff: <http://pcdm.org/file-format-types#>
    PREFIX dc: <http://purl.org/dc/elements/1.1/>

    SELECT DISTINCT ?work
    WHERE {
        ?work a pcdmworks:Work .
        ?fileset a pcdmworks:Fileset ;
                 pcdm:memberOf ?work ;
                 pcdm:hasFile ?file .
        ?file a pcdmff:HTML .
    }


----------------
Related Requests
----------------


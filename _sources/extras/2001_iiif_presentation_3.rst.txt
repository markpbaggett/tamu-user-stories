===================
IIIF Presentation 3
===================

-----------
Description
-----------

Currently, the Libraries has a IIIF presentation v2 service as part of `irIIIFService <https://github.com/TAMULib/IRIIIFService>`_.
This service creates v2 manifests and sometimes v2 collections. With presentation v3, many new features were added to the
API giving us control over how an item appears in a IIIF viewer or external to the digital collection.

-------
Request
-------

irIIIFService is either updated to support presenation v3 or a new service is created.

-------------------
Acceptance Criteria
-------------------

* Every work is represented by a v3 manifest.
* Every collection is represented by a v3 collection with references to its manifests and collections.
* Files that should be painted on a canvas are.
* Files that should supplement a canvas are.
* Files that should be apart of the rendering property are.
* Files that should be apart of a seeAlso property are.
* A homepage property links back to the original resource in its collection.
* A multi-canvased work can have a :code:`paged` behavior.
* Each canvas should have a thumbnail property to speed up load in a IIIF viewer.
* If ranges exist, they should be structured in the manifest.

-----------------
Notes or Examples
-----------------

`Map History of the 1st Armored Division <https://markpbaggett.github.io/static_iiif/manifests/service_maps_demo/service_maps_0069.json>`_
is a two canvas service map in Fedora.

`Cary's survey of the high roads from London to Hampton Court . . . <https://markpbaggett.github.io/static_iiif/manifests/brainstorming/london_maps_11.json>`_
is a book and has been :code:`paged`. Its geospatial dataset is part of the :code:`rendering` property in the manifest.

`Albert, Henry, et al, R-421 1901, 1905 <https://markpbaggett.github.io/static_iiif/manifests/tests/cherokee-freedmen-with-ranges.json>`_
is a folder with many pages. Each page has descriptive metadata.  It also has ranges that help users navigate the manifest
and its various parts. For example, a :code:`pcdmworks:FileSet` with a corresponding :code:`pcdmworks:Range` would take
the label of the Range and target the canvas that includes the FileSet:

.. code-block:: json

      "items": [
        {
          "id": "https://markpbaggett.github.io/static_iiif/manifests/tests/cherokee-freedmen-with-ranges/range/2",
          "type": "Range",
          "label": {
            "en": [
              "Envelope containing the documents for the denied Cherokee Freedmen case of Henry Albert et al."
            ]
          },
          "items": [
            {
              "id": "https://markpbaggett.github.io/static_iiif/manifests/tests/cherokee-freedmen-with-ranges/canvas/2/0",
              "type": "Canvas"
            }
          ]
        }


----------------
Related Requests
----------------

*


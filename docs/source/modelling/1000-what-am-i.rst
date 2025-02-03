=========================
File Types and Work Types
=========================

-----------
Description
-----------

Not all files or works are the same, and librarians need the ability to define the nature of a work so that it receives
appropriate treatment in terms of interoperability. For example, a GIS dataset associated with a work that includes
images should not be treated as a canvas. Instead, it should function as a downloadable binary file linked to the parent
resource. In order to do this, the most straightforward way seems to be allowing type to be stated via :code:`rdf:type`
in Fedora.

-------
Request
-------

I want to be able to state the Object that a file or work is an instance of so that it cnd be
treated differently in interoperable systems like IIIF presentation.

-------------------
Acceptance Criteria
-------------------

* A controlled set of work types are prescribed unless determined to be unneeded or unnecessary by developers.
* A controlled set of files types are adopted and those are setable by librarians on ingest.

-----------------
Notes or Examples
-----------------

`An initial document <https://tamu-cookbook.readthedocs.io/en/latest/components/0000_file_types.html>`_
was created to define file types in Fedora.  This list is derived from `PCDM File Formats <https://pcdm.org/2015/10/14/file-format-types>`_.

If deemed necessary, a similar list could be created for works.  This does not exist
as part of PCDM. At my previous institution, we created a `Files and Works Ontology <https://ontology.lib.utk.edu/works>`_
that inherited from PCDM to define various work types. These work types were stored
in a prescribed way in Fedora and had related Models in the code base surrounding our
repository that treated the work types in different ways.

----------------
Related Requests
----------------


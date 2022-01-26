================
nsIImportFilters
================

`mailnews/import/public/nsIImportFilters.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportFilters.idl>`_


Methods
=======

AutoLocate
----------

``boolean AutoLocate(aDescription, aLocation)``

Parameters
^^^^^^^^^^

* out wstring aDescription
* out :doc:`nsIFile` aLocation

Return value
^^^^^^^^^^^^

* boolean

SetLocation
-----------

``void SetLocation(aLocation)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aLocation

Import
------

``boolean Import(aError)``

Parameters
^^^^^^^^^^

* out wstring aError

Return value
^^^^^^^^^^^^

* boolean

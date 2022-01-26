=================
nsIImportSettings
=================

`mailnews/import/public/nsIImportSettings.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportSettings.idl>`_


Methods
=======

AutoLocate
----------

``boolean AutoLocate(description, location)``

Parameters
^^^^^^^^^^

* out wstring description
* out :doc:`nsIFile` location

Return value
^^^^^^^^^^^^

* boolean

SetLocation
-----------

``void SetLocation(location)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` location

Import
------

``boolean Import(localMailAccount)``

Parameters
^^^^^^^^^^

* out :doc:`nsIMsgAccount` localMailAccount

Return value
^^^^^^^^^^^^

* boolean

=================
nsIMimeMiscStatus
=================

`mailnews/mime/public/nsIMimeMiscStatus.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeMiscStatus.idl>`_


Methods
=======

GetWindowXULandJS
-----------------

``string GetWindowXULandJS()``

Return value
^^^^^^^^^^^^

* string

GetGlobalXULandJS
-----------------

``string GetGlobalXULandJS()``

Return value
^^^^^^^^^^^^

* string

GetIndividualXUL
----------------

``string GetIndividualXUL(aName, aHeader, aEmail)``

Parameters
^^^^^^^^^^

* in string aName
* in string aHeader
* in string aEmail

Return value
^^^^^^^^^^^^

* string

GetMiscStatus
-------------

``long GetMiscStatus(aName, aEmail)``

Parameters
^^^^^^^^^^

* in string aName
* in string aEmail

Return value
^^^^^^^^^^^^

* long

GetImageURL
-----------

``string GetImageURL(aStatus)``

Parameters
^^^^^^^^^^

* in long aStatus

Return value
^^^^^^^^^^^^

* string

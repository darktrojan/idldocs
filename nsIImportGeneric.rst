================
nsIImportGeneric
================

`mailnews/import/public/nsIImportGeneric.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportGeneric.idl>`_


Methods
=======

GetData
-------

``nsISupports GetData(dataId)``

Parameters
^^^^^^^^^^

* in string dataId

Return value
^^^^^^^^^^^^

* :doc:`nsISupports`

SetData
-------

``void SetData(dataId, pData)``

Parameters
^^^^^^^^^^

* in string dataId
* in :doc:`nsISupports` pData

GetStatus
---------

``long GetStatus(statusKind)``

Parameters
^^^^^^^^^^

* in string statusKind

Return value
^^^^^^^^^^^^

* long

WantsProgress
-------------

``boolean WantsProgress()``

Return value
^^^^^^^^^^^^

* boolean

BeginImport
-----------

``boolean BeginImport(successLog, errorLog)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupportsString` successLog
* in :doc:`nsISupportsString` errorLog

Return value
^^^^^^^^^^^^

* boolean

ContinueImport
--------------

``boolean ContinueImport()``

Return value
^^^^^^^^^^^^

* boolean

GetProgress
-----------

``long GetProgress()``

Return value
^^^^^^^^^^^^

* long

CancelImport
------------

``void CancelImport()``

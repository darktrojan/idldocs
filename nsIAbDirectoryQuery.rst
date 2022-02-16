===================
nsIAbDirectoryQuery
===================

`mailnews/addrbook/public/nsIAbDirectoryQuery.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbDirectoryQuery.idl>`_


Methods
=======

doQuery
-------

``long doQuery(aDirectory, aArguments, aListener, aResultLimit, aTimeOut)``

Initiates a query on a directory and sub-directories for properties
on cards

Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` aDirectory
* in :doc:`nsIAbDirectoryQueryArguments` aArguments
* in :doc:`nsIAbDirSearchListener` aListener
* in long aResultLimit
* in long aTimeOut

Return value
^^^^^^^^^^^^

* long

  A context id for the query

stopQuery
---------

``void stopQuery(contextID)``

Stops an existing query operation if
query operation is asynchronous

The nsIAbDirSearchListener will
be notified when query has stopped

It is implementation specific if notification
synchronous or asynchronous

Parameters
^^^^^^^^^^

* in long contextID

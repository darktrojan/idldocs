===================
nsIAbDirectoryQuery
===================


Methods
=======

doQuery
-------

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

Stops an existing query operation if
query operation is asynchronous
The nsIAbDirSearchListener will
be notified when query has stopped
It is implementation specific if notification
synchronous or asynchronous

Parameters
^^^^^^^^^^

* in long contextID

===================
nsIAbDirectoryQuery
===================


Methods
=======

doQuery
-------

Initiates a query on a directory and sub-directories for properties
on cards

@param aDirectory   A directory that the query may get extra details
from.

@param aArguments   The properties and values to match value could of
type nsIAbDirectoryQueryMatchItem for matches other
than ?contains?

@param aListener    The listener which will obtain individual query
results.

@param aResultLimit Limits the number of results returned to a maximum
value.

@param aTimeOut     The maximum length of time for the query

@return             A context id for the query

Parameters
^^^^^^^^^^

* ``in nsIAbDirectory aDirectory``
* ``in nsIAbDirectoryQueryArguments aArguments``
* ``in nsIAbDirSearchListener aListener``
* ``in long aResultLimit``
* ``in long aTimeOut``

Return value
^^^^^^^^^^^^

* ``long``

stopQuery
---------

Stops an existing query operation if
query operation is asynchronous

The nsIAbDirSearchListener will
be notified when query has stopped

It is implementation specific if notification
synchronous or asynchronous

@param contextID
The unique number returned from
the doQuery methods


Parameters
^^^^^^^^^^

* ``in long contextID``

Return value
^^^^^^^^^^^^

* ``void``

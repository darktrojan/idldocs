=================
nsILDAPConnection
=================

`mailnews/addrbook/public/nsILDAPConnection.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPConnection.idl>`_


Constants
=========

VERSION2
--------

**Type**: ``unsigned long``

**Value**: ``2``


VERSION3
--------

**Type**: ``unsigned long``

**Value**: ``3``


Properties
==========

errorString
-----------

``readonly attribute wstring errorString``

the string version of lderrno

bindName
--------

``readonly attribute AUTF8String bindName``

DN to bind as.  use the init() method to set this.

@exception NS_ERROR_OUT_OF_MEMORY

closure
-------

``attribute nsISupports closure``

private parameter (anything caller desires)

Methods
=======

init
----

``void init(aUrl, aBindName, aMessageListener, aClosure, aVersion)``

Set up the connection.  Note that init() must be called on a thread
that already has an nsIEventQueue.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPURL` aUrl
* in AUTF8String aBindName
* in :doc:`nsILDAPMessageListener` aMessageListener
* in :doc:`nsISupports` aClosure
* in unsigned long aVersion

Throws
^^^^^^

* NS_ERROR_ILLEGAL_VALUE        null pointer or invalid version
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_OFFLINE              we are in off-line mode
* NS_ERROR_FAILURE
* NS_ERROR_UNEXPECTED           internal error

getLdErrno
----------

``long getLdErrno(matched, s)``

Get information about the last error that occurred on this connection.

Parameters
^^^^^^^^^^

* out AUTF8String matched
* out AUTF8String s

Return value
^^^^^^^^^^^^

* long

  the error code, as defined in nsILDAPErrors.idl

=================
nsILDAPConnection
=================


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


Methods
=======

init
----

Set up the connection.  Note that init() must be called on a thread
that already has an nsIEventQueue.
@exception NS_ERROR_ILLEGAL_VALUE        null pointer or invalid version
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_OFFLINE              we are in off-line mode
@exception NS_ERROR_FAILURE
@exception NS_ERROR_UNEXPECTED           internal error

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPURL` aUrl
* in AUTF8String aBindName
* in :doc:`nsILDAPMessageListener` aMessageListener
* in :doc:`nsISupports` aClosure
* in unsigned long aVersion

getLdErrno
----------

Get information about the last error that occurred on this connection.

Parameters
^^^^^^^^^^

* out AUTF8String matched
* out AUTF8String s

Return value
^^^^^^^^^^^^

* long

  the error code, as defined in nsILDAPErrors.idl

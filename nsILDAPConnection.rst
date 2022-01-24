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

@param aUrl              A URL for the ldap server. The host, port and
ssl connection type will be extracted from this
@param aBindName         DN to bind as
@param aMessageListener  Callback for DNS resolution completion
@param aClosure          private parameter (anything caller desires)
@param aVersion          LDAP version to use (currently VERSION2 or
VERSION3)

@exception NS_ERROR_ILLEGAL_VALUE        null pointer or invalid version
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_OFFLINE              we are in off-line mode
@exception NS_ERROR_FAILURE
@exception NS_ERROR_UNEXPECTED           internal error

Parameters
^^^^^^^^^^

* ``in nsILDAPURL aUrl``
* ``in AUTF8String aBindName``
* ``in nsILDAPMessageListener aMessageListener``
* ``in nsISupports aClosure``
* ``in unsigned long aVersion``

Return value
^^^^^^^^^^^^

* ``void``

getLdErrno
----------

Get information about the last error that occurred on this connection.

@param matched   if the server is returning LDAP_NO_SUCH_OBJECT,
LDAP_ALIAS_PROBLEM, LDAP_INVALID_DN_SYNTAX,
or LDAP_ALIAS_DEREF_PROBLEM, this will contain
the portion of DN that matches the entry that is
closest to the requested entry

@param s         additional error information from the server

@return          the error code, as defined in nsILDAPErrors.idl

Parameters
^^^^^^^^^^

* ``out AUTF8String matched``
* ``out AUTF8String s``

Return value
^^^^^^^^^^^^

* ``long``

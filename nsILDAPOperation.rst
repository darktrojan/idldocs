================
nsILDAPOperation
================


Constants
=========

NO_LIMIT
--------

**Type**: ``long``

**Value**: ``0``

No time and/or size limit specified

Methods
=======

init
----

Initializes this operation.  Must be called prior to initiating
any actual operations.  Note that by default, the aMessageListener
callbacks happen on the LDAP connection thread.  If you need them
to happen on the main thread (or any other thread), then you should
created an nsISupports proxy object and pass that in.
@exception NS_ERROR_ILLEGAL_VALUE        a NULL pointer was passed in
@exception NS_ERROR_UNEXPECTED           failed to get connection handle

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPConnection` aConnection
* in :doc:`nsILDAPMessageListener` aMessageListener
* in :doc:`nsISupports` aClosure

simpleBind
----------

Asynchronously authenticate to the LDAP server.
@exception NS_ERROR_LDAP_ENCODING_ERROR  problem encoding bind request
@exception NS_ERROR_LDAP_SERVER_DOWN     server down (XXX rebinds?)
@exception NS_ERROR_LDAP_CONNECT_ERROR   connection failed or lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_UNEXPECTED           internal error

Parameters
^^^^^^^^^^

* in AUTF8String passwd

saslBind
--------

Asynchronously perform a SASL bind against the LDAP server

Parameters
^^^^^^^^^^

* in ACString service
* in ACString mechanism
* in ACString authModuleType

saslStep
--------

Continue a SASL bind operation

Parameters
^^^^^^^^^^

* in string token
* in unsigned long tokenLen

addExt
------

Kicks off an asynchronous add request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
of the LDAP protocol that the
client is using
@exception NS_ERROR_UNEXPECTED           an unexpected error has
occurred
XXX doesn't currently handle LDAPControl params

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in Array<:doc:`nsILDAPModification`> aMods

deleteExt
---------

Kicks off an asynchronous delete request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
of the LDAP protocol that the
client is using
@exception NS_ERROR_UNEXPECTED           an unexpected error has
occurred
XXX doesn't currently handle LDAPControl params

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn

modifyExt
---------

Kicks off an asynchronous modify request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
of the LDAP protocol that the
client is using
@exception NS_ERROR_UNEXPECTED           an unexpected error has
occurred
XXX doesn't currently handle LDAPControl params

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in Array<:doc:`nsILDAPModification`> aMods

rename
------

Kicks off an asynchronous rename request.
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
of the LDAP protocol that the
client is using
@exception NS_ERROR_UNEXPECTED           an unexpected error has
occurred
XXX doesn't currently handle LDAPControl params

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in AUTF8String aNewRDn
* in AUTF8String aNewParent
* in boolean aDeleteOldRDn

searchExt
---------

Kicks off an asynchronous search request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
of the LDAP protocol that the
client is using
@exception NS_ERROR_LDAP_FILTER_ERROR
@exception NS_ERROR_UNEXPECTED

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in int32_t aScope
* in AUTF8String aFilter
* in ACString aAttributes
* in PRIntervalTime aTimeOut
* in int32_t aSizeLimit

abandonExt
----------

Cancels an async operation that is in progress.
XXX controls not supported yet
@exception NS_ERROR_NOT_IMPLEMENTED      server or client controls
were set on this object
@exception NS_ERROR_NOT_INITIALIZED      operation not initialized
@exception NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
@exception NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
receive the request or the
connection was lost
@exception NS_ERROR_OUT_OF_MEMORY        out of memory
@exception NS_ERROR_INVALID_ARG          invalid argument
@exception NS_ERROR_UNEXPECTED           internal error

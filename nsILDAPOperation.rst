================
nsILDAPOperation
================

`mailnews/addrbook/public/nsILDAPOperation.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPOperation.idl>`_


Constants
=========

NO_LIMIT
--------

**Type**: ``long``

**Value**: ``0``

No time and/or size limit specified

Properties
==========

connection
----------

``readonly attribute nsILDAPConnection connection``

The connection this operation is on.

@exception NS_ERROR_ILLEGAL_VALUE        a NULL pointer was passed in

messageListener
---------------

``readonly attribute nsILDAPMessageListener messageListener``

Callback for individual result messages related to this operation (set
by the init() method).  This is actually an nsISupports proxy object,
as the callback will happen from another thread.

@exception NS_ERROR_ILLEGAL_VALUE        a NULL pointer was passed in

messageID
---------

``readonly attribute long messageID``

The message-id associated with this operation.

@exception NS_ERROR_ILLEGAL_VALUE        a NULL pointer was passed in

closure
-------

``attribute nsISupports closure``

private parameter (anything caller desires)

requestNum
----------

``attribute unsigned long requestNum``

number of the request for compare that the request is still valid.

serverControls
--------------

``attribute Array<nsILDAPControl> serverControls``

If specified, these arrays of nsILDAPControls are passed into the LDAP
C SDK for any extended operations (ie method calls on this interface
ending in "Ext").

clientControls
--------------

``attribute Array<nsILDAPControl> clientControls``

Methods
=======

init
----

``void init(aConnection, aMessageListener, aClosure)``

Initializes this operation.  Must be called prior to initiating
any actual operations.  Note that by default, the aMessageListener
callbacks happen on the LDAP connection thread.  If you need them
to happen on the main thread (or any other thread), then you should
created an nsISupports proxy object and pass that in.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPConnection` aConnection
* in :doc:`nsILDAPMessageListener` aMessageListener
* in :doc:`nsISupports` aClosure

Throws
^^^^^^

* NS_ERROR_ILLEGAL_VALUE        a NULL pointer was passed in
* NS_ERROR_UNEXPECTED           failed to get connection handle

simpleBind
----------

``void simpleBind(passwd)``

Asynchronously authenticate to the LDAP server.

Parameters
^^^^^^^^^^

* in AUTF8String passwd

Throws
^^^^^^

* NS_ERROR_LDAP_ENCODING_ERROR  problem encoding bind request
* NS_ERROR_LDAP_SERVER_DOWN     server down (XXX rebinds?)
* NS_ERROR_LDAP_CONNECT_ERROR   connection failed or lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_UNEXPECTED           internal error

saslBind
--------

``void saslBind(service, mechanism, authModuleType)``

Asynchronously perform a SASL bind against the LDAP server

Parameters
^^^^^^^^^^

* in ACString service
* in ACString mechanism
* in ACString authModuleType

saslStep
--------

``void saslStep(token, tokenLen)``

Continue a SASL bind operation

Parameters
^^^^^^^^^^

* in string token
* in unsigned long tokenLen

addExt
------

``void addExt(aBaseDn, aMods)``

Kicks off an asynchronous add request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in Array<:doc:`nsILDAPModification`> aMods

Throws
^^^^^^

* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
  of the LDAP protocol that the
  client is using
* NS_ERROR_UNEXPECTED           an unexpected error has
  occurred
  XXX doesn't currently handle LDAPControl params

deleteExt
---------

``void deleteExt(aBaseDn)``

Kicks off an asynchronous delete request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn

Throws
^^^^^^

* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
  of the LDAP protocol that the
  client is using
* NS_ERROR_UNEXPECTED           an unexpected error has
  occurred
  XXX doesn't currently handle LDAPControl params

modifyExt
---------

``void modifyExt(aBaseDn, aMods)``

Kicks off an asynchronous modify request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in Array<:doc:`nsILDAPModification`> aMods

Throws
^^^^^^

* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
  of the LDAP protocol that the
  client is using
* NS_ERROR_UNEXPECTED           an unexpected error has
  occurred
  XXX doesn't currently handle LDAPControl params

rename
------

``void rename(aBaseDn, aNewRDn, aNewParent, aDeleteOldRDn)``

Kicks off an asynchronous rename request.

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in AUTF8String aNewRDn
* in AUTF8String aNewParent
* in boolean aDeleteOldRDn

Throws
^^^^^^

* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
  of the LDAP protocol that the
  client is using
* NS_ERROR_UNEXPECTED           an unexpected error has
  occurred
  XXX doesn't currently handle LDAPControl params

searchExt
---------

``void searchExt(aBaseDn, aScope, aFilter, aAttributes, aTimeOut, aSizeLimit)``

Kicks off an asynchronous search request.  The "ext" stands for
"extensions", and is intended to convey that this method will
eventually support the extensions described in the
draft-ietf-ldapext-ldap-c-api-04.txt Internet Draft.

Parameters
^^^^^^^^^^

* in AUTF8String aBaseDn
* in int32_t aScope
* in AUTF8String aFilter
* in ACString aAttributes
* in PRIntervalTime aTimeOut
* in int32_t aSizeLimit

Throws
^^^^^^

* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        ran out of memory
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_LDAP_NOT_SUPPORTED   not supported in the version
  of the LDAP protocol that the
  client is using
* NS_ERROR_LDAP_FILTER_ERROR
* NS_ERROR_UNEXPECTED

abandonExt
----------

``void abandonExt()``

Cancels an async operation that is in progress.
XXX controls not supported yet

Throws
^^^^^^

* NS_ERROR_NOT_IMPLEMENTED      server or client controls
  were set on this object
* NS_ERROR_NOT_INITIALIZED      operation not initialized
* NS_ERROR_LDAP_ENCODING_ERROR  error during BER-encoding
* NS_ERROR_LDAP_SERVER_DOWN     the LDAP server did not
  receive the request or the
  connection was lost
* NS_ERROR_OUT_OF_MEMORY        out of memory
* NS_ERROR_INVALID_ARG          invalid argument
* NS_ERROR_UNEXPECTED           internal error

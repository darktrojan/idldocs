==============
nsILDAPMessage
==============


Constants
=========

RES_BIND
--------

**Type**: ``long``

**Value**: ``97``

Result of a bind operation

RES_SEARCH_ENTRY
----------------

**Type**: ``long``

**Value**: ``100``

An entry found in an search operation.

RES_SEARCH_REFERENCE
--------------------

**Type**: ``long``

**Value**: ``115``

An LDAPv3 search reference (a referral to another server)

RES_SEARCH_RESULT
-----------------

**Type**: ``long``

**Value**: ``101``

The result of a search operation (i.e. the search is done; no more
entries to follow).

RES_MODIFY
----------

**Type**: ``long``

**Value**: ``103``

The result of a modify operation.

RES_ADD
-------

**Type**: ``long``

**Value**: ``105``

The result of an add operation

RES_DELETE
----------

**Type**: ``long``

**Value**: ``107``

The result of a delete operation

RES_MODDN
---------

**Type**: ``long``

**Value**: ``109``

The result of an modify DN operation

RES_COMPARE
-----------

**Type**: ``long``

**Value**: ``111``

The result of a compare operation

RES_EXTENDED
------------

**Type**: ``long``

**Value**: ``120``

The result of an LDAPv3 extended operation

Properties
==========

dn
--

``readonly attribute AUTF8String dn``

The Distinguished Name of the entry associated with this message.

@exception NS_ERROR_OUT_OF_MEMORY        ran out of memory
@exception NS_ERROR_ILLEGAL_VALUE        null pointer passed in
@exception NS_ERROR_LDAP_DECODING_ERROR  problem during BER-decoding
@exception NS_ERROR_UNEXPECTED           bug or memory corruption

operation
---------

``readonly attribute nsILDAPOperation operation``

The operation this message originated from

@exception NS_ERROR_NULL_POINTER         NULL pointer to getter

errorCode
---------

``readonly attribute long errorCode``

The result code (aka lderrno) for this message.

IDL definitions for these constants live in nsILDAPErrors.idl.

@exception NS_ERROR_ILLEGAL_VALUE    null pointer passed in

type
----

``readonly attribute long type``

The result type of this message.  Possible types listed below, the
values chosen are taken from the draft-ietf-ldapext-ldap-c-api-04.txt
and are the same ones used in the ldap.h include file from the Mozilla
LDAP C SDK.

@exception NS_ERROR_ILLEGAL_VALUE    null pointer passed in
@exception NS_ERROR_UNEXPECTED       internal error (possible memory
corruption)

errorMessage
------------

``readonly attribute AUTF8String errorMessage``

Additional error information optionally sent by the server.

matchedDn
---------

``readonly attribute AUTF8String matchedDn``

In LDAPv3, when the server returns any of the following errors:
NO_SUCH_OBJECT, ALIAS_PROBLEM, INVALID_DN_SYNTAX, ALIAS_DEREF_PROBLEM,
it also returns the closest existing DN to the entry requested.

Methods
=======

getAttributes
-------------

``Array<AUTF8String> getAttributes()``

Get all the attributes in this message.
@exception NS_ERROR_OUT_OF_MEMORY
@exception NS_ERROR_ILLEGAL_VALUE        null pointer passed in
@exception NS_ERROR_UNEXPECTED           bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  problem during BER decoding

Return value
^^^^^^^^^^^^

* Array<AUTF8String>

  array of all attributes in the current message

getValues
---------

``Array<AString> getValues(attr)``

Get an array of all the attribute values in this message.
@exception NS_ERROR_UNEXPECTED           Bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  Attribute not found or other
decoding error.
@exception NS_ERROR_OUT_OF_MEMORY

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* Array<AString>

  Array of values for attr.

toUnicode
---------

``wstring toUnicode()``

get an LDIF-like string representation of this message

Return value
^^^^^^^^^^^^

* wstring

  unicode encoded string representation.

getBinaryValues
---------------

``Array<nsILDAPBERValue> getBinaryValues(attr)``

Get an array of all the attribute values in this message (a wrapper
around the LDAP C SDK's get_values_len()).
@exception NS_ERROR_UNEXPECTED           Bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  Attribute not found or other
decoding error.
@exception NS_ERROR_OUT_OF_MEMORY

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* Array<:doc:`nsILDAPBERValue`>

  Array of nsILDAPBERValue objects.

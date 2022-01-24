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

Methods
=======

getAttributes
-------------

Get all the attributes in this message.

@exception NS_ERROR_OUT_OF_MEMORY
@exception NS_ERROR_ILLEGAL_VALUE        null pointer passed in
@exception NS_ERROR_UNEXPECTED           bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  problem during BER decoding

@return  array of all attributes in the current message

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``Array``

getValues
---------

Get an array of all the attribute values in this message.

@param attr      The attribute whose values are to be returned

@exception NS_ERROR_UNEXPECTED           Bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  Attribute not found or other
decoding error.
@exception NS_ERROR_OUT_OF_MEMORY

@return  Array of values for attr.

Parameters
^^^^^^^^^^

* ``in string attr``

Return value
^^^^^^^^^^^^

* ``Array``

toUnicode
---------

get an LDIF-like string representation of this message

@return unicode encoded string representation.

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``wstring``

getBinaryValues
---------------

Get an array of all the attribute values in this message (a wrapper
around the LDAP C SDK's get_values_len()).

@param attr      The attribute whose values are to be returned

@exception NS_ERROR_UNEXPECTED           Bug or memory corruption
@exception NS_ERROR_LDAP_DECODING_ERROR  Attribute not found or other
decoding error.
@exception NS_ERROR_OUT_OF_MEMORY

@return   Array of nsILDAPBERValue objects.

Parameters
^^^^^^^^^^

* ``in string attr``

Return value
^^^^^^^^^^^^

* ``Array``

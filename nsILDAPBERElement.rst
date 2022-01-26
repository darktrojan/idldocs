=================
nsILDAPBERElement
=================

`mailnews/addrbook/public/nsILDAPBERElement.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPBERElement.idl>`_

nsILDAPBERElement is a wrapper interface for a C-SDK BerElement object.
Typically, this is used as an intermediate object to aid in the manual
construction of a BER value.  Once the construction is completed by calling
methods on this object, an nsILDAPBERValue can be retrieved from the
asValue attribute on this interface.

<http://www.mozilla.org/directory/ietf-docs/draft-ietf-ldapext-ldap-c-api-05.txt>
contains some documentation that mostly (but not exactly) matches
the code that this wraps in section 17.

Constants
=========

TAG_LBER_ERROR
--------------

**Type**: ``unsigned long``

**Value**: ``4294967295``

Most TAG_* constants can be used in the construction or passing in of
values to the aTag arguments to most of the methods in this interface.
When returned from a parsing method, 0xffffffff is referred to
has the parse-error semantic (ie TAG_LBER_ERROR); when passing it to
a construction method, it is used to mean "pick the default tag for
this type" (ie TAG_LBER_DEFAULT).

TAG_LBER_DEFAULT
----------------

**Type**: ``unsigned long``

**Value**: ``4294967295``


TAG_LBER_END_OF_SEQORSET
------------------------

**Type**: ``unsigned long``

**Value**: ``4294967294``


TAG_LBER_PRIMITIVE
------------------

**Type**: ``unsigned long``

**Value**: ``0``

BER encoding types and masks

TAG_LBER_CONSTRUCTED
--------------------

**Type**: ``unsigned long``

**Value**: ``32``

The following two tags are carried over from the LDAP C SDK; their
exact purpose there is not well documented.  They both have
the same value there as well.

TAG_LBER_ENCODING_MASK
----------------------

**Type**: ``unsigned long``

**Value**: ``32``


TAG_LBER_BIG_TAG_MASK
---------------------

**Type**: ``unsigned long``

**Value**: ``31``


TAG_LBER_MORE_TAG_MASK
----------------------

**Type**: ``unsigned long``

**Value**: ``128``


TAG_LBER_BOOLEAN
----------------

**Type**: ``unsigned long``

**Value**: ``1``

general BER types we know about

TAG_LBER_INTEGER
----------------

**Type**: ``unsigned long``

**Value**: ``2``


TAG_LBER_BITSTRING
------------------

**Type**: ``unsigned long``

**Value**: ``3``


TAG_LBER_OCTETSTRING
--------------------

**Type**: ``unsigned long``

**Value**: ``4``


TAG_LBER_NULL
-------------

**Type**: ``unsigned long``

**Value**: ``5``


TAG_LBER_ENUMERATED
-------------------

**Type**: ``unsigned long``

**Value**: ``10``


TAG_LBER_SEQUENCE
-----------------

**Type**: ``unsigned long``

**Value**: ``48``


TAG_LBER_SET
------------

**Type**: ``unsigned long``

**Value**: ``49``


Properties
==========

asValue
-------

``readonly attribute nsILDAPBERValue asValue``

an nsILDAPBERValue version of this element.  Calls ber_flatten() under
the hood.

@exception NS_ERROR_OUT_OF_MEMORY

Methods
=======

init
----

``void init(aValue)``

Initialize this object.  Must be called before calling any other method
on this interface.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPBERValue` aValue

  value to preinitialize with; 0 for a new empty object

Throws
^^^^^^

* NS_ERROR_NOT_IMPLEMENTED  preinitialization is currently
  not implemented
* NS_ERROR_OUT_OF_MEMORY    unable to allocate the internal
  BerElement

putString
---------

``unsigned long putString(aString, aTag)``

Write a string to this element.

Parameters
^^^^^^^^^^

* in AUTF8String aString

  string to write
* in unsigned long aTag

  tag for this string (if TAG_LBER_DEFAULT is used,
  TAG_LBER_OCTETSTRING will be written).

Return value
^^^^^^^^^^^^

* unsigned long

  number of bytes written

Throws
^^^^^^

* NS_ERROR_FAILUE   C-SDK returned error

startSet
--------

``void startSet(aTag)``

Start a set.  Sets may be nested.

Parameters
^^^^^^^^^^

* in unsigned long aTag

  tag for this set (if TAG_LBER_DEFAULT is used,
  TAG_LBER_SET will be written).

Throws
^^^^^^

* NS_ERROR_FAILUE   C-SDK returned an error

putSet
------

``unsigned long putSet()``

Cause the entire set started by the last startSet() call to be written.

Return value
^^^^^^^^^^^^

* unsigned long

  number of bytes written

Throws
^^^^^^

* NS_ERROR_FAILUE   C-SDK returned an error

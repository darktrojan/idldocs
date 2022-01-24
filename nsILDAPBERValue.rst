===============
nsILDAPBERValue
===============

Representation of a BER value as an interface containing an array of
bytes.  Someday this should perhaps be obsoleted by a better, more
generalized version of nsIByteBuffer, but that's currently not even
scriptable (see bug 125596).

Methods
=======

set
---

Set the BER value from an array of bytes (copies).

@exception NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

Parameters
^^^^^^^^^^

* ``in Array<octet> aValue``

Return value
^^^^^^^^^^^^

* ``void``

setFromUTF8
-----------

Set the BER value from a UTF8 string (copies).

@exception NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

Parameters
^^^^^^^^^^

* ``in AUTF8String aValue``

Return value
^^^^^^^^^^^^

* ``void``

get
---

Get the BER value as an array of bytes.  Note that if this value is
zero-length, aCount and aRetVal will both be 0.  This means that
(in C++ anyway) the caller MUST test either aCount or aRetval before
dereferencing aRetVal.

@exception NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``Array``

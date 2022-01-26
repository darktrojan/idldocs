===============
nsILDAPBERValue
===============

`mailnews/addrbook/public/nsILDAPBERValue.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPBERValue.idl>`_

Representation of a BER value as an interface containing an array of
bytes.  Someday this should perhaps be obsoleted by a better, more
generalized version of nsIByteBuffer, but that's currently not even
scriptable (see bug 125596).

Methods
=======

set
---

``void set(aValue)``

Set the BER value from an array of bytes (copies).

Parameters
^^^^^^^^^^

* in Array<octet> aValue

Throws
^^^^^^

* NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

setFromUTF8
-----------

``void setFromUTF8(aValue)``

Set the BER value from a UTF8 string (copies).

Parameters
^^^^^^^^^^

* in AUTF8String aValue

Throws
^^^^^^

* NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

get
---

``Array<octet> get()``

Get the BER value as an array of bytes.  Note that if this value is
zero-length, aCount and aRetVal will both be 0.  This means that
(in C++ anyway) the caller MUST test either aCount or aRetval before
dereferencing aRetVal.

Return value
^^^^^^^^^^^^

* Array<octet>

Throws
^^^^^^

* NS_ERROR_OUT_OF_MEMORY    couldn't allocate buffer to copy to

==============
nsILDAPService
==============

`mailnews/addrbook/public/nsILDAPService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPService.idl>`_

This interface is a catch-all for any LDAP functionality that is needed
in XPCOM and not provided elsewhere.

Methods
=======

createFilter
------------

``AUTF8String createFilter(aMaxSize, aPattern, aPrefix, aSuffix, aAttr, aValue)``

Generates and returns an LDAP search filter by substituting
aValue, aAttr, aPrefix, and aSuffix into aPattern.
Exposes the functionality of ldap_create_filter() via XPCOM.
There is some documentation on the filter template format
(passed in via aPattern) here:
https://docs.oracle.com/cd/E19957-01/817-6707/filter.html

Parameters
^^^^^^^^^^

* in unsigned long aMaxSize
* in AUTF8String aPattern
* in AUTF8String aPrefix
* in AUTF8String aSuffix
* in AUTF8String aAttr
* in AUTF8String aValue

Return value
^^^^^^^^^^^^

* AUTF8String

Throws
^^^^^^

* NS_ERROR_INVALID_ARG      invalid parameter passed in
* NS_ERROR_OUT_OF_MEMORY    allocation failed
* NS_ERROR_NOT_AVAILABLE    filter longer than maxsiz chars
* NS_ERROR_UNEXPECTED       ldap_create_filter returned
  unexpected error code

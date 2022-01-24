==========
nsILDAPURL
==========

Strings in methods inherited from nsIURI, which are using XPIDL
|string| types, are expected to be UTF8 encoded. All such strings
in this interface, except attribute types (e.g. "cn"), should in fact
be UTF8. It's important to remember that attributes can not be UTF8,
they can only be of a limited subset of ASCII (see RFC 2251).

Constants
=========

SCOPE_BASE
----------

**Type**: ``long``

**Value**: ``0``

Search just the base object

SCOPE_ONELEVEL
--------------

**Type**: ``long``

**Value**: ``1``

Search only the children of the base object

SCOPE_SUBTREE
-------------

**Type**: ``long``

**Value**: ``2``

Search the entire subtree under and including the base object

OPT_SECURE
----------

**Type**: ``unsigned long``

**Value**: ``1``

If this is set/true, this is an ldaps: URL, not an ldap: URL

Methods
=======

init
----

Initialize an LDAP URL

Parameters
^^^^^^^^^^

* ``in unsigned long aUrlType``
* ``in long aDefaultPort``
* ``in AUTF8String aSpec``
* ``in string aOriginCharset``
* ``in nsIURI aBaseURI``

Return value
^^^^^^^^^^^^

* ``void``

addAttribute
------------

Add one attribute to the array of attributes to request. If the
attribute is already in our array, this becomes a noop.

Parameters
^^^^^^^^^^

* ``in ACString aAttribute``

Return value
^^^^^^^^^^^^

* ``void``

removeAttribute
---------------

Remove one attribute from the array of attributes to request. If
the attribute didn't exist in the array, this becomes a noop.
@exception NS_ERROR_OUT_OF_MEMORY    Ran out of memory

Parameters
^^^^^^^^^^

* ``in ACString aAttribute``

Return value
^^^^^^^^^^^^

* ``void``

hasAttribute
------------

Test if an attribute is in our list of attributes already
@exception NS_ERROR_NULL_POINTER     NULL pointer to GET method

Parameters
^^^^^^^^^^

* ``in ACString aAttribute``

Return value
^^^^^^^^^^^^

* ``boolean``
  boolean                      Truth value

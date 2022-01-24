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

Properties
==========

dn
--

``attribute AUTF8String dn``

The distinguished name of the URL (ie the base DN for the search).
This string is expected to be a valid UTF8 string.

for the getter:

@exception NS_ERROR_NULL_POINTER     NULL pointer to GET method
@exception NS_ERROR_OUT_OF_MEMORY    Ran out of memory

attributes
----------

``attribute ACString attributes``

The attributes to get for this URL, in comma-separated format. If the
list is empty, all attributes are requested.

scope
-----

``attribute long scope``

The scope of the search.  defaults to SCOPE_BASE.

@exception NS_ERROR_NULL_POINTER     NULL pointer to GET method
@exception NS_ERROR_MALFORMED_URI    Illegal base to SET method

filter
------

``attribute AUTF8String filter``

The search filter. "(objectClass=*)" is the default.

options
-------

``attribute unsigned long options``

Any options defined for this URL (check options using a bitwise and)

@exception NS_ERROR_NULL_POINTER     NULL pointer to GET method
@exception NS_ERROR_OUT_OF_MEMORY    Ran out of memory

Methods
=======

init
----

``void init(aUrlType, aDefaultPort, aSpec, aOriginCharset, aBaseURI)``

Initialize an LDAP URL

Parameters
^^^^^^^^^^

* in unsigned long aUrlType
* in long aDefaultPort
* in AUTF8String aSpec
* in string aOriginCharset
* in :doc:`nsIURI` aBaseURI

addAttribute
------------

``void addAttribute(aAttribute)``

Add one attribute to the array of attributes to request. If the
attribute is already in our array, this becomes a noop.

Parameters
^^^^^^^^^^

* in ACString aAttribute

removeAttribute
---------------

``void removeAttribute(aAttribute)``

Remove one attribute from the array of attributes to request. If
the attribute didn't exist in the array, this becomes a noop.
@exception NS_ERROR_OUT_OF_MEMORY    Ran out of memory

Parameters
^^^^^^^^^^

* in ACString aAttribute

hasAttribute
------------

``boolean hasAttribute(aAttribute)``

Test if an attribute is in our list of attributes already
@exception NS_ERROR_NULL_POINTER     NULL pointer to GET method

Parameters
^^^^^^^^^^

* in ACString aAttribute

Return value
^^^^^^^^^^^^

* boolean

  boolean                      Truth value

======================
nsILDAPURLParserResult
======================

`mailnews/addrbook/public/nsILDAPURL.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPURL.idl>`_

A structure to represent an LDAP URL.

Properties
==========

host
----

``readonly attribute AUTF8String host``

The host name of the URL. */

port
----

``readonly attribute long port``

The port number of the URL. */

dn
--

``readonly attribute AUTF8String dn``

The distinguished name of the URL. */

attributes
----------

``readonly attribute ACString attributes``

The attributes to request when searching. */

scope
-----

``readonly attribute long scope``

The scope to use when searching. */

filter
------

``readonly attribute AUTF8String filter``

The filter to use when searching. */

options
-------

``readonly attribute unsigned long options``

The options of the URL. */

============================
nsIAbDirectoryQueryArguments
============================

`mailnews/addrbook/public/nsIAbDirectoryQuery.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbDirectoryQuery.idl>`_

The arguments for a query.

Contains an expression for perform matches
and an array of properties which should be
returned if a match is found from the expression


Properties
==========

expression
----------

``attribute nsISupports expression``

Defines the boolean expression for
the matching of cards


querySubDirectories
-------------------

``attribute boolean querySubDirectories``

Defines if sub directories should be
queried


typeSpecificArg
---------------

``attribute nsISupports typeSpecificArg``

A parameter which can be used to pass in data specific to a particular
type of addressbook.

filter
------

``attribute AUTF8String filter``

A custom search filter which user wants to use in LDAP query.

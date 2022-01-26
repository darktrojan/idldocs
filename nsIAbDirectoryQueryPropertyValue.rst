================================
nsIAbDirectoryQueryPropertyValue
================================

`mailnews/addrbook/public/nsIAbDirectoryQuery.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbDirectoryQuery.idl>`_


Properties
==========

name
----

``readonly attribute string name``

The property which should be matched

For example 'primaryEmail' or 'homePhone'
for card properties.

Two further properties are defined that
do not exist as properties on a card.

'card:nsIAbCard' which represents the interface
of a card component


value
-----

``readonly attribute wstring value``

The value of the property


valueISupports
--------------

``readonly attribute nsISupports valueISupports``

The value of the property
as an interface

Only valid if the corresponding
property name is related to an
interface instead of a wstring


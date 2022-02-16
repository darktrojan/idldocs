=====================
nsIAbLDAPAttributeMap
=====================

`mailnews/addrbook/public/nsIAbLDAPAttributeMap.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbLDAPAttributeMap.idl>`_

A mapping between addressbook properties and ldap attributes.

Each addressbook property can map to one or more attributes.  If
there is no entry in preferences for a field, the getters generally
return null; empty strings are passed through as usual. The intent is
that properties with a non-zero number of attributes can be overridden for
a specific server by supplying a zero-length string.  For this to work,
most callers are likely to want to check for both success and a
non-empty string.

Note that the one exception to this pattern is getAttributes, which
throws NS_ERROR_FAILURE for non-existent property entries, since
XPConnect doesn't like returning null arrays.

Note that each LDAP attribute can map to at most one addressbook
property.  The checkState method is a useful tool in enforcing
this.  Failure to enforce it may make it impossible to guarantee
that getProperty will do something consistent and reasonable.

Maybe someday once we support ldap autoconfig stuff (ie
draft-joslin-config-schema-11.txt), we can simplify this and other
code and only allow a property to map to a single attribute.

Methods
=======

getAttributeList
----------------

``ACString getAttributeList(aProperty)``

Get all the LDAP attributes associated with a given property
name, in order of precedence (highest to lowest).

Parameters
^^^^^^^^^^

* in ACString aProperty

  the address book property to return attrs for

Return value
^^^^^^^^^^^^

* ACString

  a comma-separated list of attributes, null if no entry is
  present

getAttributes
-------------

``Array<ACString> getAttributes(aProperty)``

Get all the LDAP attributes associated with a given property name, in
order of precedence (highest to lowest).

Parameters
^^^^^^^^^^

* in ACString aProperty

  the address book property to return attrs for

Return value
^^^^^^^^^^^^

* Array<ACString>

  an array of attributes

Throws
^^^^^^

* NS_ERROR_FAILURE if there is no entry for this property

getFirstAttribute
-----------------

``ACString getFirstAttribute(aProperty)``

Get the first (canonical) LDAP attribute associated with a given property
name

Parameters
^^^^^^^^^^

* in ACString aProperty

  the address book property to return attrs for

Return value
^^^^^^^^^^^^

* ACString

  the first attribute associated with a given property,
  null if there is no entry for this property

setAttributeList
----------------

``void setAttributeList(aProperty, aAttributeList, allowInconsistencies)``

Set an existing mapping to the comma-separated list of attributes.

Parameters
^^^^^^^^^^

* in ACString aProperty
* in ACString aAttributeList
* in boolean allowInconsistencies

Throws
^^^^^^

* NS_ERROR_FAILURE    making this change would result in a map
  with an LDAP attribute pointing to more
  than one property

getProperty
-----------

``ACString getProperty(aAttribute)``

Find the Mozilla addressbook property name that this attribute should
map to.

Parameters
^^^^^^^^^^

* in ACString aAttribute

Return value
^^^^^^^^^^^^

* ACString

  the addressbook property name, null if it's not used in the map

getAllCardAttributes
--------------------

``ACString getAllCardAttributes()``

Get all attributes that may be used in an addressbook card via this
property map (used for passing to to an LDAP search when you want
everything that could be in a card returned).

Return value
^^^^^^^^^^^^

* ACString

  a comma-separated list of attribute names

Throws
^^^^^^

* NS_ERROR_FAILURE  there are no attributes in this property map

getAllCardProperties
--------------------

``Array<ACString> getAllCardProperties()``

Get all properties that may be used in an addressbook card via this
property map.

Return value
^^^^^^^^^^^^

* Array<ACString>

  an array of properties

Throws
^^^^^^

* NS_ERROR_FAILURE  there are no attributes in this property map

checkState
----------

``void checkState()``

Check that no LDAP attributes are listed in more than one property.

Throws
^^^^^^

* NS_ERROR_FAILURE    one or more LDAP attributes are listed
  multiple times.  The object is now in an
  inconsistent state, and should be either
  manually repaired or discarded.

setFromPrefs
------------

``void setFromPrefs(aPrefBranchName)``

Set any attributes specified in the given prefbranch on this object.

Parameters
^^^^^^^^^^

* in ACString aPrefBranchName

Throws
^^^^^^

* NS_ERROR_FAILURE    one or more LDAP attributes are listed
  multiple times.  The object is now in an
  inconsistent state, and should be either
  manually repaired or discarded.

setCardPropertiesFromLDAPMessage
--------------------------------

``void setCardPropertiesFromLDAPMessage(aMessage, aCard)``

Set the properties on an addressbook card from the given LDAP message
using the map in this object.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPMessage` aMessage

  is the LDAP message to get the values from

* in :doc:`nsIAbCard` aCard

  is the card object whose values are to be set

Throws
^^^^^^

* NS_ERROR_FAILURE is thrown if no addressbook properties
  are found in the message

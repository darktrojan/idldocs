=====================
nsIAbLDAPAttributeMap
=====================

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

Get all the LDAP attributes associated with a given property
name, in order of precedence (highest to lowest).

@param       aProperty   the address book property to return attrs for

@return      a comma-separated list of attributes, null if no entry is
present

Parameters
^^^^^^^^^^

* ``in ACString aProperty``

Return value
^^^^^^^^^^^^

* ``ACString``

getAttributes
-------------

Get all the LDAP attributes associated with a given property name, in
order of precedence (highest to lowest).

@param       aProperty   the address book property to return attrs for

@return      an array of attributes

@exception   NS_ERROR_FAILURE if there is no entry for this property

Parameters
^^^^^^^^^^

* ``in ACString aProperty``

Return value
^^^^^^^^^^^^

* ``Array``

getFirstAttribute
-----------------

Get the first (canonical) LDAP attribute associated with a given property
name

@param       aProperty   the address book property to return attrs for

@return      the first attribute associated with a given property,
null if there is no entry for this property

Parameters
^^^^^^^^^^

* ``in ACString aProperty``

Return value
^^^^^^^^^^^^

* ``ACString``

setAttributeList
----------------

Set an existing mapping to the comma-separated list of attributes.

@param aProperty               the mozilla addressbook property name

@param aAttributeList          a comma-separated list of attributes in
order of precedence from high to low

@param aAllowInconsistencies   allow changes that would result in
a map with an LDAP attribute associated
with more than one property.  Useful for
doing a bunch of sets at once, and
calling checkState at the end.

@exception NS_ERROR_FAILURE    making this change would result in a map
with an LDAP attribute pointing to more
than one property

Parameters
^^^^^^^^^^

* ``in ACString aProperty``
* ``in ACString aAttributeList``
* ``in boolean allowInconsistencies``

Return value
^^^^^^^^^^^^

* ``void``

getProperty
-----------

Find the Mozilla addressbook property name that this attribute should
map to.

@return the addressbook property name, null if it's not used in the map

Parameters
^^^^^^^^^^

* ``in ACString aAttribute``

Return value
^^^^^^^^^^^^

* ``ACString``

getAllCardAttributes
--------------------

Get all attributes that may be used in an addressbook card via this
property map (used for passing to to an LDAP search when you want
everything that could be in a card returned).

@return                      a comma-separated list of attribute names

@exception NS_ERROR_FAILURE  there are no attributes in this property map

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``ACString``

getAllCardProperties
--------------------

Get all properties that may be used in an addressbook card via this
property map.

@return                      an array of properties

@exception NS_ERROR_FAILURE  there are no attributes in this property map

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``Array``

checkState
----------

Check that no LDAP attributes are listed in more than one property.

@exception NS_ERROR_FAILURE    one or more LDAP attributes are listed
multiple times.  The object is now in an
inconsistent state, and should be either
manually repaired or discarded.

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``void``

setFromPrefs
------------

Set any attributes specified in the given prefbranch on this object.

@param aPrefBranchName         the pref branch containing all the
property names

@exception NS_ERROR_FAILURE    one or more LDAP attributes are listed
multiple times.  The object is now in an
inconsistent state, and should be either
manually repaired or discarded.

Parameters
^^^^^^^^^^

* ``in ACString aPrefBranchName``

Return value
^^^^^^^^^^^^

* ``void``

setCardPropertiesFromLDAPMessage
--------------------------------

Set the properties on an addressbook card from the given LDAP message
using the map in this object.

@param       aCard is the card object whose values are to be set
@param       aMessage is the LDAP message to get the values from

@exception   NS_ERROR_FAILURE is thrown if no addressbook properties
are found in the message

Parameters
^^^^^^^^^^

* ``in nsILDAPMessage aMessage``
* ``in nsIAbCard aCard``

Return value
^^^^^^^^^^^^

* ``void``

============================
nsIAbLDAPAttributeMapService
============================

The nsIAbLDAPAttributeMapService is used to build and hold a cache
of maps.

Methods
=======

getMapForPrefBranch
-------------------

Accessor to construct or return a cached copy of the attribute
map for a given preference branch.  The map is constructed by
first taking the default map (as specified by the
"ldap_2.servers.default.attrmap" prefbranch), and then having any
preferences specified by aPrefBranchName override the defaults.
LDIF import and export code should use the default map.

@return      the requested map

@exception   NS_ERROR_FAILURE    error constructing the map;
possibly because of a failure
from checkState()

Parameters
^^^^^^^^^^

* ``in ACString aPrefBranchName``

Return value
^^^^^^^^^^^^

* ``nsIAbLDAPAttributeMap``

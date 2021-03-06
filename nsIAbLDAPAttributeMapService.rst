============================
nsIAbLDAPAttributeMapService
============================

`mailnews/addrbook/public/nsIAbLDAPAttributeMap.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbLDAPAttributeMap.idl>`_

The nsIAbLDAPAttributeMapService is used to build and hold a cache
of maps.

Methods
=======

getMapForPrefBranch
-------------------

``nsIAbLDAPAttributeMap getMapForPrefBranch(aPrefBranchName)``

Accessor to construct or return a cached copy of the attribute
map for a given preference branch.  The map is constructed by
first taking the default map (as specified by the
"ldap_2.servers.default.attrmap" prefbranch), and then having any
preferences specified by aPrefBranchName override the defaults.
LDIF import and export code should use the default map.

Parameters
^^^^^^^^^^

* in ACString aPrefBranchName

Return value
^^^^^^^^^^^^

* :doc:`nsIAbLDAPAttributeMap`

  the requested map

Throws
^^^^^^

* NS_ERROR_FAILURE    error constructing the map;
  possibly because of a failure
  from checkState()

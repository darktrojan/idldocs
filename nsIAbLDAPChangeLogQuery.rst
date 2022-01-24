=======================
nsIAbLDAPChangeLogQuery
=======================


Methods
=======

queryAuthDN
-----------

Starts an LDAP query to find auth DN

Parameters
^^^^^^^^^^

* in AUTF8String aValueUsedToFindDn

queryRootDSE
------------

Starts an LDAP query to search server's Root DSE

queryChangeLog
--------------

Starts an LDAP ChangeLog query to find changelog entries

Parameters
^^^^^^^^^^

* in AUTF8String aChangeLogDN
* in int32_t aLastChangeNo

queryChangedEntries
-------------------

Starts an LDAP query to find changed entries

Parameters
^^^^^^^^^^

* in AUTF8String aChangedEntryDN

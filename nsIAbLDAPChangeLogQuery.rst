=======================
nsIAbLDAPChangeLogQuery
=======================

`mailnews/addrbook/public/nsIAbLDAPReplicationQuery.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbLDAPReplicationQuery.idl>`_


Methods
=======

queryAuthDN
-----------

``void queryAuthDN(aValueUsedToFindDn)``

Starts an LDAP query to find auth DN

Parameters
^^^^^^^^^^

* in AUTF8String aValueUsedToFindDn

queryRootDSE
------------

``void queryRootDSE()``

Starts an LDAP query to search server's Root DSE

queryChangeLog
--------------

``void queryChangeLog(aChangeLogDN, aLastChangeNo)``

Starts an LDAP ChangeLog query to find changelog entries

Parameters
^^^^^^^^^^

* in AUTF8String aChangeLogDN
* in int32_t aLastChangeNo

queryChangedEntries
-------------------

``void queryChangedEntries(aChangedEntryDN)``

Starts an LDAP query to find changed entries

Parameters
^^^^^^^^^^

* in AUTF8String aChangedEntryDN

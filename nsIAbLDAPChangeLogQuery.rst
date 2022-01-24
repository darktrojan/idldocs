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

* ``in AUTF8String aValueUsedToFindDn``

Return value
^^^^^^^^^^^^

* ``void``

queryRootDSE
------------

Starts an LDAP query to search server's Root DSE

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``void``

queryChangeLog
--------------

Starts an LDAP ChangeLog query to find changelog entries

Parameters
^^^^^^^^^^

* ``in AUTF8String aChangeLogDN``
* ``in int32_t aLastChangeNo``

Return value
^^^^^^^^^^^^

* ``void``

queryChangedEntries
-------------------

Starts an LDAP query to find changed entries

Parameters
^^^^^^^^^^

* ``in AUTF8String aChangedEntryDN``

Return value
^^^^^^^^^^^^

* ``void``

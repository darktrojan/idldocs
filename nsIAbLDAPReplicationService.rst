===========================
nsIAbLDAPReplicationService
===========================

this service does replication of an LDAP directory to a local AB Database.

Methods
=======

startReplication
----------------

Start Replication of given LDAP directory represented by the URI

Parameters
^^^^^^^^^^

* ``in nsIAbLDAPDirectory aDirectory``
* ``in nsIWebProgressListener progressListener``

Return value
^^^^^^^^^^^^

* ``void``

cancelReplication
-----------------

Cancel Replication of given LDAP directory represented by the URI

Parameters
^^^^^^^^^^

* ``in nsIAbLDAPDirectory aDirectory``

Return value
^^^^^^^^^^^^

* ``void``

done
----

callback when replication is done, failure or success

Parameters
^^^^^^^^^^

* ``in boolean aSuccess``

Return value
^^^^^^^^^^^^

* ``void``

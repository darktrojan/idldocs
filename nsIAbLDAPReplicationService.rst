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

* in :doc:`nsIAbLDAPDirectory` aDirectory
* in :doc:`nsIWebProgressListener` progressListener

cancelReplication
-----------------

Cancel Replication of given LDAP directory represented by the URI

Parameters
^^^^^^^^^^

* in :doc:`nsIAbLDAPDirectory` aDirectory

done
----

callback when replication is done, failure or success

Parameters
^^^^^^^^^^

* in boolean aSuccess

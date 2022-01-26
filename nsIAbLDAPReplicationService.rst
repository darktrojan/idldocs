===========================
nsIAbLDAPReplicationService
===========================

`mailnews/addrbook/public/nsIAbLDAPReplicationService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbLDAPReplicationService.idl>`_

this service does replication of an LDAP directory to a local AB Database.

Methods
=======

startReplication
----------------

``void startReplication(aDirectory, progressListener)``

Start Replication of given LDAP directory represented by the URI

Parameters
^^^^^^^^^^

* in :doc:`nsIAbLDAPDirectory` aDirectory
* in :doc:`nsIWebProgressListener` progressListener

cancelReplication
-----------------

``void cancelReplication(aDirectory)``

Cancel Replication of given LDAP directory represented by the URI

Parameters
^^^^^^^^^^

* in :doc:`nsIAbLDAPDirectory` aDirectory

done
----

``void done(aSuccess)``

callback when replication is done, failure or success

Parameters
^^^^^^^^^^

* in boolean aSuccess

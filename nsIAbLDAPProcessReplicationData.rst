===============================
nsIAbLDAPProcessReplicationData
===============================

this service does replication of an LDAP directory to a local AB Database.

Constants
=========

kIdle
-----

**Type**: ``long``

**Value**: ``0``

replication states

kAnonymousBinding
-----------------

**Type**: ``long``

**Value**: ``1``


kAuthenticatedBinding
---------------------

**Type**: ``long``

**Value**: ``2``


kSyncServerBinding
------------------

**Type**: ``long``

**Value**: ``3``


kSearchingAuthDN
----------------

**Type**: ``long``

**Value**: ``4``


kDecidingProtocol
-----------------

**Type**: ``long``

**Value**: ``5``


kAuthenticating
---------------

**Type**: ``long``

**Value**: ``6``


kReplicatingAll
---------------

**Type**: ``long``

**Value**: ``7``


kSearchingRootDSE
-----------------

**Type**: ``long``

**Value**: ``8``


kFindingChanges
---------------

**Type**: ``long``

**Value**: ``9``


kReplicatingChanges
-------------------

**Type**: ``long``

**Value**: ``10``


kReplicationDone
----------------

**Type**: ``long``

**Value**: ``11``


Properties
==========

replicationState
----------------

``readonly attribute int32_t replicationState``

readonly attribute giving the current replication state

Methods
=======

init
----

``void init(directory, connection, url, query, progressListener)``

this method initializes the implementation

Parameters
^^^^^^^^^^

* in :doc:`nsIAbLDAPDirectory` directory
* in :doc:`nsILDAPConnection` connection
* in :doc:`nsILDAPURL` url
* in :doc:`nsIAbLDAPReplicationQuery` query
* in :doc:`nsIWebProgressListener` progressListener

abort
-----

``void abort()``

this method a aborts the ongoing processing

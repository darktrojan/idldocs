=========================
nsIAbLDAPReplicationQuery
=========================

this interface provides methods to perform LDAP Replication Queries

Methods
=======

init
----

``void init(aDirectory, aProgressListener)``

initialize for the query

Parameters
^^^^^^^^^^

* in :doc:`nsIAbLDAPDirectory` aDirectory
* in :doc:`nsIWebProgressListener` aProgressListener

doReplicationQuery
------------------

``void doReplicationQuery()``

Starts an LDAP query to do replication as needed

cancelQuery
-----------

``void cancelQuery()``

Cancels the currently executing query

done
----

``void done(aSuccess)``

this method is the callback when query is done, failed or successful

Parameters
^^^^^^^^^^

* in boolean aSuccess

=========================
nsIAbLDAPReplicationQuery
=========================

this interface provides methods to perform LDAP Replication Queries

Methods
=======

init
----

initialize for the query

Parameters
^^^^^^^^^^

* ``in nsIAbLDAPDirectory aDirectory``
* ``in nsIWebProgressListener aProgressListener``

Return value
^^^^^^^^^^^^

* ``void``

doReplicationQuery
------------------

Starts an LDAP query to do replication as needed

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``void``

cancelQuery
-----------

Cancels the currently executing query

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``void``

done
----

this method is the callback when query is done, failed or successful

Parameters
^^^^^^^^^^

* ``in boolean aSuccess``

Return value
^^^^^^^^^^^^

* ``void``

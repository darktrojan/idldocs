================
nsILDAPSyncQuery
================


Methods
=======

getQueryResults
---------------

getQueryResults

Create a new LDAP connection do a synchronous LDAP search and return
the results.
@param aServerURL - LDAP URL with parameters to a LDAP search
("ldap://host/base?attributes?one/sub?filter")
@param aProtocolVersion - LDAP protocol version to use for connection
(nsILDAPConnection.idl has symbolic constants)
@return results

Parameters
^^^^^^^^^^

* ``in nsILDAPURL aServerURL``
* ``in unsigned long aProtocolVersion``

Return value
^^^^^^^^^^^^

* ``wstring``

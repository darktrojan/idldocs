================
nsILDAPSyncQuery
================

`mailnews/addrbook/public/nsILDAPSyncQuery.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPSyncQuery.idl>`_


Methods
=======

getQueryResults
---------------

``wstring getQueryResults(aServerURL, aProtocolVersion)``

getQueryResults

Create a new LDAP connection do a synchronous LDAP search and return
the results.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPURL` aServerURL
* in unsigned long aProtocolVersion

Return value
^^^^^^^^^^^^

* wstring

  results

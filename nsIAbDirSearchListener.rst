======================
nsIAbDirSearchListener
======================

Listener callbacks for addressbook nsIAbDirectory searches and queries.

Methods
=======

onSearchFoundCard
-----------------

Invoked for each matching result found by the search.

@param aCard  A matching addressbook card.

Parameters
^^^^^^^^^^

* ``in nsIAbCard aCard``

Return value
^^^^^^^^^^^^

* ``void``

onSearchFinished
----------------

Invoked when the search finishes.

@param status   The result of the search. NS_OK means the search
completed without error. NS_ERROR_ABORT means the user
stopped the search. But there are many other error codes
which may be seen here (LDAP or NSS errors, for example).
@param complete Whether this search returned all possible results.
@param secInfo  If status is an NSS error code, the securityInfo of the
failing operation is passed out here. This can be used
to obtain a failing certificate, to present the user an
option to add it as a security exception (handy for
LDAP servers with self-signed certs).
@param location If status is an NSS error code, this holds the location
of the failed operation ("<host>:<port>").

Parameters
^^^^^^^^^^

* ``in nsresult status``
* ``in bool complete``
* ``in nsITransportSecurityInfo secInfo``
* ``in ACString location``

Return value
^^^^^^^^^^^^

* ``void``

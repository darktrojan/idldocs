======================
nsILDAPMessageListener
======================

A callback interface to be implemented by any objects that want to
receive results from an nsILDAPOperation (ie nsILDAPMessages) as they
come in.

Methods
=======

onLDAPInit
----------

Invoked when Init has completed successfully LDAP operations can
proceed.

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``void``

onLDAPMessage
-------------

Messages from LDAP operations are passed back via this function.

@param aMessage  The message that was returned, NULL if none was.

XXX semantics of NULL?

Parameters
^^^^^^^^^^

* ``in nsILDAPMessage aMessage``

Return value
^^^^^^^^^^^^

* ``void``

onLDAPError
-----------

Indicates that an error has occured - either during init, or due to
an LDAP operation.

@param status   The error code.
@param secInfo  The securityInfo object for the connection, if status
is a security (NSS) error. Null otherwise.
@param location If status is an NSS error code, this holds the location
of the failed operation ("<host>:<port>").

Parameters
^^^^^^^^^^

* ``in nsresult status``
* ``in nsITransportSecurityInfo secInfo``
* ``in ACString location``

Return value
^^^^^^^^^^^^

* ``void``

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

Parameters
^^^^^^^^^^

* ``in nsresult status``
* ``in nsITransportSecurityInfo secInfo``
* ``in ACString location``

Return value
^^^^^^^^^^^^

* ``void``

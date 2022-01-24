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

onLDAPMessage
-------------

Messages from LDAP operations are passed back via this function.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPMessage` aMessage

onLDAPError
-----------

Indicates that an error has occured - either during init, or due to
an LDAP operation.

Parameters
^^^^^^^^^^

* in nsresult status
* in :doc:`nsITransportSecurityInfo` secInfo
* in ACString location

======================
nsILDAPMessageListener
======================

`mailnews/addrbook/public/nsILDAPMessageListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPMessageListener.idl>`_

A callback interface to be implemented by any objects that want to
receive results from an nsILDAPOperation (ie nsILDAPMessages) as they
come in.

Methods
=======

onLDAPInit
----------

``void onLDAPInit()``

Invoked when Init has completed successfully LDAP operations can
proceed.

onLDAPMessage
-------------

``void onLDAPMessage(aMessage)``

Messages from LDAP operations are passed back via this function.

Parameters
^^^^^^^^^^

* in :doc:`nsILDAPMessage` aMessage

onLDAPError
-----------

``void onLDAPError(status, secInfo, location)``

Indicates that an error has occured - either during init, or due to
an LDAP operation.

Parameters
^^^^^^^^^^

* in nsresult status
* in :doc:`nsITransportSecurityInfo` secInfo
* in ACString location

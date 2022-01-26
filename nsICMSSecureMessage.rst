===================
nsICMSSecureMessage
===================

`mailnews/extensions/smime/nsICMSSecureMessage.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSSecureMessage.idl>`_

nsICMSManager (service)
Interface to access users certificate store

Methods
=======

canBeUsedForEmailEncryption
---------------------------

``bool canBeUsedForEmailEncryption(cert)``

Return true if the certificate can be used for encrypting emails.

Parameters
^^^^^^^^^^

* in :doc:`nsIX509Cert` cert

Return value
^^^^^^^^^^^^

* bool

canBeUsedForEmailSigning
------------------------

``bool canBeUsedForEmailSigning(cert)``

Return true if the certificate can be used for signing emails.

Parameters
^^^^^^^^^^

* in :doc:`nsIX509Cert` cert

Return value
^^^^^^^^^^^^

* bool

=====================
nsIMsgSMIMEHeaderSink
=====================

`mailnews/extensions/smime/nsIMsgSMIMEHeaderSink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsIMsgSMIMEHeaderSink.idl>`_


Methods
=======

signedStatus
------------

``void signedStatus(aNestingLevel, aSignatureStatus, aSignerCert, aMsgNeckoURL)``

Parameters
^^^^^^^^^^

* in long aNestingLevel
* in long aSignatureStatus
* in :doc:`nsIX509Cert` aSignerCert
* in AUTF8String aMsgNeckoURL

encryptionStatus
----------------

``void encryptionStatus(aNestingLevel, aEncryptionStatus, aReceipientCert, aMsgNeckoURL)``

Parameters
^^^^^^^^^^

* in long aNestingLevel
* in long aEncryptionStatus
* in :doc:`nsIX509Cert` aReceipientCert
* in AUTF8String aMsgNeckoURL

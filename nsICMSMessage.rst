=============
nsICMSMessage
=============

`mailnews/extensions/smime/nsICMSMessage.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSMessage.idl>`_

nsICMSMessage
Interface to a CMS Message

Methods
=======

contentIsSigned
---------------

``void contentIsSigned(aSigned)``

Parameters
^^^^^^^^^^

* out boolean aSigned

contentIsEncrypted
------------------

``void contentIsEncrypted(aEncrypted)``

Parameters
^^^^^^^^^^

* out boolean aEncrypted

getSignerCommonName
-------------------

``void getSignerCommonName(aName)``

Parameters
^^^^^^^^^^

* out string aName

getSignerEmailAddress
---------------------

``void getSignerEmailAddress(aEmail)``

Parameters
^^^^^^^^^^

* out string aEmail

getSignerCert
-------------

``void getSignerCert(scert)``

Parameters
^^^^^^^^^^

* out :doc:`nsIX509Cert` scert

getEncryptionCert
-----------------

``void getEncryptionCert(ecert)``

Parameters
^^^^^^^^^^

* out :doc:`nsIX509Cert` ecert

verifySignature
---------------

``void verifySignature()``

verifyDetachedSignature
-----------------------

``void verifyDetachedSignature(aDigestData, aDigestType)``

Parameters
^^^^^^^^^^

* in Array<octet> aDigestData
* in int16_t aDigestType

CreateEncrypted
---------------

``void CreateEncrypted(aRecipientCerts)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIX509Cert`> aRecipientCerts

CreateSigned
------------

``void CreateSigned(scert, ecert, aDigestData, aDigestType)``

Parameters
^^^^^^^^^^

* in :doc:`nsIX509Cert` scert
* in :doc:`nsIX509Cert` ecert
* in Array<octet> aDigestData
* in int16_t aDigestType

asyncVerifySignature
--------------------

``void asyncVerifySignature(listener)``

Async version of nsICMSMessage::VerifySignature.
Code will be executed on a background thread and
availability of results will be notified using a
call to nsISMimeVerificationListener.

Parameters
^^^^^^^^^^

* in :doc:`nsISMimeVerificationListener` listener

asyncVerifyDetachedSignature
----------------------------

``void asyncVerifyDetachedSignature(listener, aDigestData, aDigestType)``

Async version of nsICMSMessage::VerifyDetachedSignature.
Code will be executed on a background thread and
availability of results will be notified using a
call to nsISMimeVerificationListener.

Set aDigestType to one of the values from nsICryptoHash.

Parameters
^^^^^^^^^^

* in :doc:`nsISMimeVerificationListener` listener
* in Array<octet> aDigestData
* in int16_t aDigestType

===================
nsIMsgComposeSecure
===================

`mailnews/compose/public/nsIMsgComposeSecure.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgComposeSecure.idl>`_


Properties
==========

signMessage
-----------

``attribute boolean signMessage``

Set to true if the outgoing message shall be signed.

requireEncryptMessage
---------------------

``attribute boolean requireEncryptMessage``

Set to true if the outgoing message shall be encrypted.

Methods
=======

requiresCryptoEncapsulation
---------------------------

``boolean requiresCryptoEncapsulation(aIdentity, aCompFields)``

*************************************************************************
The following functions are called during message creation by nsMsgSend,
after the message source is completely prepared.
**************************************************************************/
Determine if encryption and/or signing is required.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aIdentity
* in :doc:`nsIMsgCompFields` aCompFields

Return value
^^^^^^^^^^^^

* boolean

  - Returns true if the creation of the message requires us to go through
  some encryption work, and false otherwise.

beginCryptoEncapsulation
------------------------

``void beginCryptoEncapsulation(aStream, aRecipients, aCompFields, aIdentity, sendReport, aIsDraft)``

Start encryption work. Called before the encrypted data is processed.

Parameters
^^^^^^^^^^

* in :doc:`nsIOutputStream` aStream
* in string aRecipients
* in :doc:`nsIMsgCompFields` aCompFields
* in :doc:`nsIMsgIdentity` aIdentity
* in :doc:`nsIMsgSendReport` sendReport
* in boolean aIsDraft

mimeCryptoWriteBlock
--------------------

``void mimeCryptoWriteBlock(aBuf, aLen)``

Process a part of the message data. Called multiple times, usually for every
line of the data to be encrypted

Parameters
^^^^^^^^^^

* in string aBuf
* in long aLen

finishCryptoEncapsulation
-------------------------

``void finishCryptoEncapsulation(aAbort, sendReport)``

End encryption work. Called after the encrypted data is processed.

Parameters
^^^^^^^^^^

* in boolean aAbort
* in :doc:`nsIMsgSendReport` sendReport

findCertByEmailAddress
----------------------

``nsIX509Cert findCertByEmailAddress(aEmailAddress, aRequireValidCert)``

Find a certificate by email address.

(Note: This function is used primarily for testing purposes. It runs
on the main thread, which may cause nested event loop spinning.)
(TODO: A better place for this might be nsISMimeJSHelper.idl,
but it would require to move the C++ implementation.)

Parameters
^^^^^^^^^^

* in ACString aEmailAddress
* in boolean aRequireValidCert

Return value
^^^^^^^^^^^^

* :doc:`nsIX509Cert`

  The matching certificate if found.

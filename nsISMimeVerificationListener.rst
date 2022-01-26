============================
nsISMimeVerificationListener
============================

`mailnews/extensions/smime/nsICMSMessage.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSMessage.idl>`_


Methods
=======

notify
------

``void notify(verifiedMessage, verificationResultCode)``

Notify that results are ready, that have been requested
using nsICMSMessage::asyncVerify[Detached]Signature()
verificationResultCode matches synchronous result code from
nsICMSMessage::verify[Detached]Signature

Parameters
^^^^^^^^^^

* in :doc:`nsICMSMessage` verifiedMessage
* in nsresult verificationResultCode

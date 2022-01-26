============================
nsIEncryptedSMIMEURIsService
============================

`mailnews/extensions/smime/nsIEncryptedSMIMEURIsSrvc.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsIEncryptedSMIMEURIsSrvc.idl>`_


Methods
=======

rememberEncrypted
-----------------

``void rememberEncrypted(uri)``

Parameters
^^^^^^^^^^

* in AUTF8String uri

forgetEncrypted
---------------

``void forgetEncrypted(uri)``

Parameters
^^^^^^^^^^

* in AUTF8String uri

isEncrypted
-----------

``boolean isEncrypted(uri)``

Parameters
^^^^^^^^^^

* in AUTF8String uri

Return value
^^^^^^^^^^^^

* boolean

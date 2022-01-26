=================
nsIUserCertPicker
=================

`mailnews/extensions/smime/nsIUserCertPicker.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsIUserCertPicker.idl>`_


Methods
=======

pickByUsage
-----------

``nsIX509Cert pickByUsage(ctx, selectedNickname, certUsage, allowInvalid, allowDuplicateNicknames, emailAddress, canceled)``

Parameters
^^^^^^^^^^

* in :doc:`nsIInterfaceRequestor` ctx
* in wstring selectedNickname
* in long certUsage
* in boolean allowInvalid
* in boolean allowDuplicateNicknames
* in AString emailAddress
* out boolean canceled

Return value
^^^^^^^^^^^^

* :doc:`nsIX509Cert`

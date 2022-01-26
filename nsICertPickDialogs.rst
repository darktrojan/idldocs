==================
nsICertPickDialogs
==================

`mailnews/extensions/smime/nsICertPickDialogs.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICertPickDialogs.idl>`_

nsICertPickDialogs provides a generic UI for choosing a certificate.

Methods
=======

pickCertificate
---------------

``void pickCertificate(ctx, certNickList, certDetailsList, selectedIndex, canceled)``

General purpose certificate prompter.

Parameters
^^^^^^^^^^

* in :doc:`nsIInterfaceRequestor` ctx
* in Array<AString> certNickList
* in Array<AString> certDetailsList
* inout long selectedIndex
* out boolean canceled

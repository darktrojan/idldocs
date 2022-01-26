=====================
nsIImapHeaderXferInfo
=====================

`mailnews/imap/public/nsIImapHeaderXferInfo.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapHeaderXferInfo.idl>`_


Properties
==========

numHeaders
----------

``readonly attribute long numHeaders``

Methods
=======

getHeader
---------

``nsIImapHeaderInfo getHeader(hdrIndex)``

Parameters
^^^^^^^^^^

* in long hdrIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIImapHeaderInfo`

=================
nsIImapHeaderInfo
=================

`mailnews/imap/public/nsIImapHeaderXferInfo.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapHeaderXferInfo.idl>`_


Properties
==========

msgUid
------

``attribute nsMsgKey msgUid``

msgSize
-------

``attribute long msgSize``

Methods
=======

getMsgHdrs
----------

``void getMsgHdrs(aMsgHdrs)``

Parameters
^^^^^^^^^^

* out string aMsgHdrs

cacheLine
---------

``void cacheLine(line, uid)``

Parameters
^^^^^^^^^^

* in string line
* in unsigned long uid

resetCache
----------

``void resetCache()``

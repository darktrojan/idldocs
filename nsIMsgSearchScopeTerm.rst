=====================
nsIMsgSearchScopeTerm
=====================

`mailnews/search/public/nsIMsgSearchScopeTerm.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchScopeTerm.idl>`_


Properties
==========

folder
------

``readonly attribute nsIMsgFolder folder``

searchSession
-------------

``readonly attribute nsIMsgSearchSession searchSession``

Methods
=======

getInputStream
--------------

``nsIInputStream getInputStream(aHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdr

Return value
^^^^^^^^^^^^

* :doc:`nsIInputStream`

closeInputStream
----------------

``void closeInputStream()``

==================
nsIMsgSearchNotify
==================

`mailnews/search/public/nsIMsgSearchNotify.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchNotify.idl>`_


Methods
=======

onSearchHit
-----------

``void onSearchHit(header, folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` header
* in :doc:`nsIMsgFolder` folder

onSearchDone
------------

``void onSearchDone(status)``

Parameters
^^^^^^^^^^

* in nsresult status

onNewSearch
-----------

``void onNewSearch()``

===================
nsIMsgSearchAdapter
===================

`mailnews/search/public/nsIMsgSearchAdapter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchAdapter.idl>`_


Properties
==========

encoding
--------

``readonly attribute string encoding``

Methods
=======

ValidateTerms
-------------

``void ValidateTerms()``

Search
------

``void Search(done)``

Parameters
^^^^^^^^^^

* out boolean done

SendUrl
-------

``void SendUrl()``

CurrentUrlDone
--------------

``void CurrentUrlDone(exitCode)``

Parameters
^^^^^^^^^^

* in nsresult exitCode

AddHit
------

``void AddHit(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

AddResultElement
----------------

``void AddResultElement(aHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdr

OpenResultElement
-----------------

``void OpenResultElement(element)``

Parameters
^^^^^^^^^^

* in nsMsgResultElement element

ModifyResultElement
-------------------

``void ModifyResultElement(element, value)``

Parameters
^^^^^^^^^^

* in nsMsgResultElement element
* in nsMsgSearchValue value

FindTargetFolder
----------------

``nsIMsgFolder FindTargetFolder(element)``

Parameters
^^^^^^^^^^

* in nsMsgResultElement element

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

Abort
-----

``void Abort()``

getSearchCharsets
-----------------

``void getSearchCharsets(srcCharset, destCharset)``

Parameters
^^^^^^^^^^

* out AString srcCharset
* out AString destCharset

clearScope
----------

``void clearScope()``

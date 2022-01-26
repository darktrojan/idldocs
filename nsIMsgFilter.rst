============
nsIMsgFilter
============

`mailnews/search/public/nsIMsgFilter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilter.idl>`_


Properties
==========

filterType
----------

``attribute nsMsgFilterTypeType filterType``

temporary
---------

``attribute boolean temporary``

some filters are "temporary".  For example, the filters we create when the user
filters return receipts to the Sent folder.
we don't show temporary filters in the UI
and we don't write them to disk.

enabled
-------

``attribute boolean enabled``

filterName
----------

``attribute AString filterName``

filterDesc
----------

``attribute ACString filterDesc``

unparsedBuffer
--------------

``attribute ACString unparsedBuffer``

unparseable
-----------

``attribute boolean unparseable``

filterList
----------

``attribute nsIMsgFilterList filterList``

searchTerms
-----------

``attribute Array<nsIMsgSearchTerm> searchTerms``

scope
-----

``attribute nsIMsgSearchScopeTerm scope``

actionCount
-----------

``readonly attribute unsigned long actionCount``

sortedActionList
----------------

``readonly attribute Array<nsIMsgRuleAction> sortedActionList``

Methods
=======

AddTerm
-------

``void AddTerm(attrib, op, value, BooleanAND, arbitraryHeader)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op
* in :doc:`nsIMsgSearchValue` value
* in boolean BooleanAND
* in ACString arbitraryHeader

GetTerm
-------

``void GetTerm(termIndex, attrib, op, value, BooleanAND, arbitraryHeader)``

Parameters
^^^^^^^^^^

* in long termIndex
* out nsMsgSearchAttribValue attrib
* out nsMsgSearchOpValue op
* out :doc:`nsIMsgSearchValue` value
* out boolean BooleanAND
* out ACString arbitraryHeader

appendTerm
----------

``void appendTerm(term)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchTerm` term

createTerm
----------

``nsIMsgSearchTerm createTerm()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgSearchTerm`

MatchHdr
--------

``boolean MatchHdr(msgHdr, folder, db, headers)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in :doc:`nsIMsgFolder` folder
* in :doc:`nsIMsgDatabase` db
* in ACString headers

Return value
^^^^^^^^^^^^

* boolean

logRuleHit
----------

``void logRuleHit(aFilterAction, aHeader)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgRuleAction` aFilterAction
* in :doc:`nsIMsgDBHdr` aHeader

logRuleHitFail
--------------

``void logRuleHitFail(aFilterAction, aHeader, aRcode, aErrmsg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgRuleAction` aFilterAction
* in :doc:`nsIMsgDBHdr` aHeader
* in nsresult aRcode
* in AUTF8String aErrmsg

createAction
------------

``nsIMsgRuleAction createAction()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgRuleAction`

getActionAt
-----------

``nsIMsgRuleAction getActionAt(aIndex)``

Parameters
^^^^^^^^^^

* in unsigned long aIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgRuleAction`

getActionIndex
--------------

``long getActionIndex(aAction)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgRuleAction` aAction

Return value
^^^^^^^^^^^^

* long

appendAction
------------

``void appendAction(action)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgRuleAction` action

clearActionList
---------------

``void clearActionList()``

SaveToTextFile
--------------

``void SaveToTextFile(aStream)``

Parameters
^^^^^^^^^^

* in :doc:`nsIOutputStream` aStream

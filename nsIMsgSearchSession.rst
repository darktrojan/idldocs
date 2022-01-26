===================
nsIMsgSearchSession
===================

`mailnews/search/public/nsIMsgSearchSession.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchSession.idl>`_


Constants
=========

onNewSearch
-----------

**Type**: ``long``

**Value**: ``1``

@name Search notification flags
These flags determine which notifications will be sent.
@{

onSearchDone
------------

**Type**: ``long``

**Value**: ``2``


onSearchHit
-----------

**Type**: ``long``

**Value**: ``4``


allNotifications
----------------

**Type**: ``long``

**Value**: ``7``


BooleanOR
---------

**Type**: ``long``

**Value**: ``0``


BooleanAND
----------

**Type**: ``long``

**Value**: ``1``


Properties
==========

searchTerms
-----------

``attribute Array<nsIMsgSearchTerm> searchTerms``

numSearchTerms
--------------

``readonly attribute unsigned long numSearchTerms``

runningAdapter
--------------

``readonly attribute nsIMsgSearchAdapter runningAdapter``

numResults
----------

``readonly attribute long numResults``

window
------

``attribute nsIMsgWindow window``

Methods
=======

addSearchTerm
-------------

``void addSearchTerm(attrib, op, value, BooleanAND, customString)``

add a search term to the search session

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib

  search attribute (e.g. nsMsgSearchAttrib::Subject)
* in nsMsgSearchOpValue op

  search operator (e.g. nsMsgSearchOp::Contains)
* in :doc:`nsIMsgSearchValue` value

  search value (e.g. "Dogbert", see nsIMsgSearchValue)
* in boolean BooleanAND

  set to true if associated boolean operator is AND
* in string customString

  if attrib > nsMsgSearchAttrib::OtherHeader,
  a user defined arbitrary header
  if attrib == nsMsgSearchAttrib::Custom, the custom id
  otherwise ignored

createTerm
----------

``nsIMsgSearchTerm createTerm()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgSearchTerm`

appendTerm
----------

``void appendTerm(term)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchTerm` term

registerListener
----------------

``void registerListener(aListener, aNotifyFlags)``

@} */
Add a listener to get notified of search starts, stops, and hits.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchNotify` aListener
* in long aNotifyFlags

unregisterListener
------------------

``void unregisterListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchNotify` listener

getNthSearchTerm
----------------

``void getNthSearchTerm(whichTerm, attrib, op, value)``

Parameters
^^^^^^^^^^

* in long whichTerm
* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op
* in :doc:`nsIMsgSearchValue` value

countSearchScopes
-----------------

``long countSearchScopes()``

Return value
^^^^^^^^^^^^

* long

getNthSearchScope
-----------------

``void getNthSearchScope(which, scopeId, folder)``

Parameters
^^^^^^^^^^

* in long which
* out nsMsgSearchScopeValue scopeId
* out :doc:`nsIMsgFolder` folder

addScopeTerm
------------

``void addScopeTerm(scope, folder)``

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope
* in :doc:`nsIMsgFolder` folder

addDirectoryScopeTerm
---------------------

``void addDirectoryScopeTerm(scope)``

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope

clearScopes
-----------

``void clearScopes()``

ScopeUsesCustomHeaders
----------------------

``boolean ScopeUsesCustomHeaders(scope, selection, forFilters)``

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope
* in voidPtr selection
* in boolean forFilters

Return value
^^^^^^^^^^^^

* boolean

IsStringAttribute
-----------------

``boolean IsStringAttribute(attrib)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib

Return value
^^^^^^^^^^^^

* boolean

AddAllScopes
------------

``void AddAllScopes(attrib)``

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue attrib

search
------

``void search(aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow

interruptSearch
---------------

``void interruptSearch()``

pauseSearch
-----------

``void pauseSearch()``

resumeSearch
------------

``void resumeSearch()``

MatchHdr
--------

``boolean MatchHdr(aMsgHdr, aDatabase)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in :doc:`nsIMsgDatabase` aDatabase

Return value
^^^^^^^^^^^^

* boolean

addSearchHit
------------

``void addSearchHit(header, folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` header
* in :doc:`nsIMsgFolder` folder

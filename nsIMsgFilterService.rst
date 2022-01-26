===================
nsIMsgFilterService
===================

`mailnews/search/public/nsIMsgFilterService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterService.idl>`_


Methods
=======

OpenFilterList
--------------

``nsIMsgFilterList OpenFilterList(filterFile, rootFolder, msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` filterFile
* in :doc:`nsIMsgFolder` rootFolder
* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

CloseFilterList
---------------

``void CloseFilterList(filterList)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` filterList

SaveFilterList
--------------

``void SaveFilterList(filterList, filterFile)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` filterList
* in :doc:`nsIFile` filterFile

CancelFilterList
----------------

``void CancelFilterList(filterList)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` filterList

getTempFilterList
-----------------

``nsIMsgFilterList getTempFilterList(aFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

applyFiltersToFolders
---------------------

``void applyFiltersToFolders(aFilterList, aFolders, aMsgWindow, aCallback)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` aFilterList
* in Array<:doc:`nsIMsgFolder`> aFolders
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgOperationListener` aCallback

applyFilters
------------

``void applyFilters(aFilterType, aMsgHdrList, aFolder, aMsgWindow, aCallback)``

Apply filters to a specific list of messages in a folder.

Parameters
^^^^^^^^^^

* in nsMsgFilterTypeType aFilterType

  The type of filter to match against
* in Array<:doc:`nsIMsgDBHdr`> aMsgHdrList

  The list of message headers (nsIMsgDBHdr objects)
* in :doc:`nsIMsgFolder` aFolder

  The folder the messages belong to
* in :doc:`nsIMsgWindow` aMsgWindow

  A UI window for attaching progress/dialogs
* in :doc:`nsIMsgOperationListener` aCallback

  A listener that gets notified of any filtering error

addCustomAction
---------------

``void addCustomAction(aAction)``

Add a custom filter action.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterCustomAction` aAction

  the custom action to add

getCustomActions
----------------

``Array<nsIMsgFilterCustomAction> getCustomActions()``

get the list of custom actions

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgFilterCustomAction`>

  an array of nsIMsgFilterCustomAction objects

getCustomAction
---------------

``nsIMsgFilterCustomAction getCustomAction(id)``

Lookup a custom action given its id.

Parameters
^^^^^^^^^^

* in ACString id

  unique identifier for a particular custom action

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterCustomAction`

  the custom action, or null if not found

addCustomTerm
-------------

``void addCustomTerm(aTerm)``

Add a custom search term.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchCustomTerm` aTerm

  the custom term to add

getCustomTerms
--------------

``Array<nsIMsgSearchCustomTerm> getCustomTerms()``

get the list of custom search terms

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgSearchCustomTerm`>

  an array of nsIMsgSearchCustomTerm objects

getCustomTerm
-------------

``nsIMsgSearchCustomTerm getCustomTerm(id)``

Lookup a custom search term given its id.

Parameters
^^^^^^^^^^

* in ACString id

  unique identifier for a particular custom search term

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgSearchCustomTerm`

  the custom search term, or null if not found

filterTypeName
--------------

``ACString filterTypeName(filterType)``

Translate the filter type flag into human readable type names.
In case of multiple flag they are delimited by '&'.

Parameters
^^^^^^^^^^

* in nsMsgFilterTypeType filterType

  nsMsgFilterType flags of filter type

Return value
^^^^^^^^^^^^

* ACString

  A string describing the filter type.

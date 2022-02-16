============
nsIMsgDBView
============

`mailnews/base/public/nsIMsgDBView.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgDBView.idl>`_


Properties
==========

viewType
--------

``readonly attribute nsMsgViewTypeValue viewType``

viewFlags
---------

``attribute nsMsgViewFlagsTypeValue viewFlags``

sortType
--------

``attribute nsMsgViewSortTypeValue sortType``

Assigning to this value does not induce a sort; use the sort() method! */

sortOrder
---------

``readonly attribute nsMsgViewSortOrderValue sortOrder``

secondarySortType
-----------------

``attribute nsMsgViewSortTypeValue secondarySortType``

Reflects the current secondary sort when a secondary sort is in effect.
If the primary sort is by date or id, the value of this attribute is moot.
Assigning to this value does not induce a sort; use the sort() method once
to set your secondary sort, then use it again to set your primary sort.
The only conceivable reason to write to this value is if you have a
grouped view where you want to affect the sort order of the (secondary)
date sort.  (Secondary sort is always by date for grouped views.)

secondarySortOrder
------------------

``attribute nsMsgViewSortOrderValue secondarySortOrder``

Reflects the current secondary sort order.
Assigning to this value does not induce a sort; use the sort() method for
all primary and secondary sort needs.  The only reason to assign to this
value is to affect the secondary sort of a grouped view.

keyForFirstSelectedMessage
--------------------------

``readonly attribute nsMsgKey keyForFirstSelectedMessage``

viewIndexForFirstSelectedMsg
----------------------------

``readonly attribute nsMsgViewIndex viewIndexForFirstSelectedMsg``

msgFolder
---------

``readonly attribute nsIMsgFolder msgFolder``

viewFolder
----------

``attribute nsIMsgFolder viewFolder``

URIForFirstSelectedMessage
--------------------------

``readonly attribute AUTF8String URIForFirstSelectedMessage``

hdrForFirstSelectedMessage
--------------------------

``readonly attribute nsIMsgDBHdr hdrForFirstSelectedMessage``

numSelected
-----------

``readonly attribute unsigned long numSelected``

The number of selected messages.  If the
"mail.operate_on_msgs_in_collapsed_threads" preference is enabled, then
any collapsed thread roots that are selected will also conceptually have
all of the messages in that thread selected.

msgToSelectAfterDelete
----------------------

``readonly attribute nsMsgViewIndex msgToSelectAfterDelete``

currentlyDisplayedMessage
-------------------------

``readonly attribute nsMsgViewIndex currentlyDisplayedMessage``

numMsgsInView
-------------

``readonly attribute long numMsgsInView``

Number of messages in view, including messages in collapsed threads.
Not currently implemented for threads with unread or watched threads
with unread.

suppressMsgDisplay
------------------

``attribute boolean suppressMsgDisplay``

suppressCommandUpdating
-----------------------

``attribute boolean suppressCommandUpdating``

suppressChangeNotifications
---------------------------

``attribute boolean suppressChangeNotifications``

Suppress change notifications. This is faster than Begin/EndUpdateBatch
on the tree, but less safe in that you're responsible for row invalidation
and row count changes.

db
--

``readonly attribute nsIMsgDatabase db``

supportsThreading
-----------------

``readonly attribute boolean supportsThreading``

searchSession
-------------

``attribute nsIMsgSearchSession searchSession``

removeRowOnMoveOrDelete
-----------------------

``readonly attribute boolean removeRowOnMoveOrDelete``

usingLines
----------

``readonly attribute boolean usingLines``

curCustomColumn
---------------

``attribute AString curCustomColumn``

The custom column to use for sorting purposes (when sort type is
nsMsgViewSortType.byCustom.)

secondaryCustomColumn
---------------------

``readonly attribute AString secondaryCustomColumn``

The custom column used for a secondary sort, blank if secondarySort is
not byCustom. The secondary sort design is such that the desired secondary
is sorted first, followed by sort by desired primary. The secondary is
read only, as it is set internally according to this design.

Methods
=======

setJSTree
---------

``void setJSTree(tree)``

A shim of XULTreeElement, with only the methods called by nsMsgDBView. */

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgJSTree` tree

open
----

``void open(folder, sortType, sortOrder, viewFlags, count)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in nsMsgViewSortTypeValue sortType
* in nsMsgViewSortOrderValue sortOrder
* in nsMsgViewFlagsTypeValue viewFlags
* out long count

openWithHdrs
------------

``void openWithHdrs(aHeaders, aSortType, aSortOrder, aViewFlags, aCount)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgEnumerator` aHeaders
* in nsMsgViewSortTypeValue aSortType
* in nsMsgViewSortOrderValue aSortOrder
* in nsMsgViewFlagsTypeValue aViewFlags
* out long aCount

close
-----

``void close()``

init
----

``void init(aMessengerInstance, aMsgWindow, aCommandUpdater)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMessenger` aMessengerInstance
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgDBViewCommandUpdater` aCommandUpdater

sort
----

``void sort(sortType, sortOrder)``

Parameters
^^^^^^^^^^

* in nsMsgViewSortTypeValue sortType
* in nsMsgViewSortOrderValue sortOrder

doCommand
---------

``void doCommand(command)``

Parameters
^^^^^^^^^^

* in nsMsgViewCommandTypeValue command

doCommandWithFolder
-------------------

``void doCommandWithFolder(command, destFolder)``

Parameters
^^^^^^^^^^

* in nsMsgViewCommandTypeValue command
* in :doc:`nsIMsgFolder` destFolder

getCommandStatus
----------------

``void getCommandStatus(command, selectable_p, selected_p)``

Parameters
^^^^^^^^^^

* in nsMsgViewCommandTypeValue command
* out boolean selectable_p
* out nsMsgViewCommandCheckStateValue selected_p

viewNavigate
------------

``void viewNavigate(motion, resultId, resultIndex, threadIndex, wrap)``

this method will automatically expand the destination thread,
if needs be.

Parameters
^^^^^^^^^^

* in nsMsgNavigationTypeValue motion
* out nsMsgKey resultId
* out nsMsgViewIndex resultIndex
* out nsMsgViewIndex threadIndex
* in boolean wrap

navigateStatus
--------------

``boolean navigateStatus(motion)``

Indicates if navigation of the passed motion type is valid.

Parameters
^^^^^^^^^^

* in nsMsgNavigationTypeValue motion

Return value
^^^^^^^^^^^^

* boolean

getKeyAt
--------

``nsMsgKey getKeyAt(index)``

Parameters
^^^^^^^^^^

* in nsMsgViewIndex index

Return value
^^^^^^^^^^^^

* nsMsgKey

getFlagsAt
----------

``unsigned long getFlagsAt(aIndex)``

Get the view flags at the passed in index.

@ return - 32 bit view flags (e.g., elided)

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex

Return value
^^^^^^^^^^^^

* unsigned long

getMsgHdrAt
-----------

``nsIMsgDBHdr getMsgHdrAt(aIndex)``

Get the msg hdr at the passed in index

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

  - msg hdr at the passed in index

Throws
^^^^^^

* - NS_MSG_INVALID_DBVIEW_INDEX

getFolderForViewIndex
---------------------

``nsIMsgFolder getFolderForViewIndex(index)``

Parameters
^^^^^^^^^^

* in nsMsgViewIndex index

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

getURIForViewIndex
------------------

``ACString getURIForViewIndex(index)``

Parameters
^^^^^^^^^^

* in nsMsgViewIndex index

Return value
^^^^^^^^^^^^

* ACString

cloneDBView
-----------

``nsIMsgDBView cloneDBView(aMessengerInstance, aMsgWindow, aCommandUpdater)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMessenger` aMessengerInstance
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgDBViewCommandUpdater` aCommandUpdater

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBView`

getSelectedMsgHdrs
------------------

``Array<nsIMsgDBHdr> getSelectedMsgHdrs()``

Provides a list of the message headers for the currently selected messages.
If the "mail.operate_on_msgs_in_collapsed_threads" preference is enabled,
then any collapsed thread roots that are selected will also (conceptually)
have all of the messages in that thread selected and they will be included
in the returned list. The one exception to this is if the front end fails
to summarize the selection, and we fall back to just displaying a single
message. In that case, we won't include the children of the collapsed
thread. However, the numSelected attribute will count those children,
because the summarizeSelection code uses that to know that it should
try to summarize the selection.

If the user has right-clicked on a message, this will return that message
(and any collapsed children if so enabled) and not the selection prior to
the right-click.

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgDBHdr`>

  an array containing the selected message headers.  You are free to
  mutate the array; it will not affect the underlying selection.

getURIsForSelection
-------------------

``Array<AUTF8String> getURIsForSelection()``

Return value
^^^^^^^^^^^^

* Array<AUTF8String>

getIndicesForSelection
----------------------

``Array<nsMsgViewIndex> getIndicesForSelection()``

Return value
^^^^^^^^^^^^

* Array<nsMsgViewIndex>

loadMessageByMsgKey
-------------------

``void loadMessageByMsgKey(aMsgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey

loadMessageByViewIndex
----------------------

``void loadMessageByViewIndex(aIndex)``

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex

loadMessageByUrl
----------------

``void loadMessageByUrl(aUrl)``

Parameters
^^^^^^^^^^

* in string aUrl

reloadMessage
-------------

``void reloadMessage()``

reloadMessageWithAllParts
-------------------------

``void reloadMessageWithAllParts()``

selectMsgByKey
--------------

``void selectMsgByKey(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

selectFolderMsgByKey
--------------------

``void selectFolderMsgByKey(aFolder, aKey)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in nsMsgKey aKey

onDeleteCompleted
-----------------

``void onDeleteCompleted(succeeded)``

Parameters
^^^^^^^^^^

* in boolean succeeded

findIndexFromKey
----------------

``nsMsgViewIndex findIndexFromKey(aMsgKey, aExpand)``

Finds the view index of the passed in msgKey. Note this should not
be called on cross-folder views since the msgKey may not be unique.

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey
* in boolean aExpand

Return value
^^^^^^^^^^^^

* nsMsgViewIndex

  - view index of msg hdr, -1 if hdr not found.

findIndexOfMsgHdr
-----------------

``nsMsgViewIndex findIndexOfMsgHdr(aMsgHdr, aExpand)``

Finds the view index of the passed in msgHdr.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in boolean aExpand

Return value
^^^^^^^^^^^^

* nsMsgViewIndex

  - view index of msg hdr, -1 if hdr not found.

ExpandAndSelectThreadByIndex
----------------------------

``void ExpandAndSelectThreadByIndex(aIndex, aAugment)``

Expands a thread and selects all it's member messages.

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex
* in boolean aAugment

getThreadContainingIndex
------------------------

``nsIMsgThread getThreadContainingIndex(aIndex)``

This method returns the nsIMsgThread object containing the header displayed
at the desired row. For grouped views and cross folder saved searches,
this will be the view thread, not the db thread.

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgThread`

  the thread object at the requested view index

insertTreeRows
--------------

``void insertTreeRows(aIndex, aNumRows, aKey, aFlags, aLevel, aFolder)``

Insert rows into the view. The caller should use NoteChange() below to
update the view.

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex
* in unsigned long aNumRows
* in nsMsgKey aKey
* in nsMsgViewFlagsTypeValue aFlags
* in unsigned long aLevel
* in :doc:`nsIMsgFolder` aFolder

removeTreeRows
--------------

``void removeTreeRows(aIndex, aNumRows)``

Remove rows from the view.  The caller should use NoteChange() below to
update the view.

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aIndex
* in unsigned long aNumRows

NoteChange
----------

``void NoteChange(aFirstLineChanged, aNumRows, aChangeType)``

Notify tree that rows have changed.

Parameters
^^^^^^^^^^

* in nsMsgViewIndex aFirstLineChanged
* in long aNumRows
* in nsMsgViewNotificationCodeValue aChangeType

getThreadContainingMsgHdr
-------------------------

``nsIMsgThread getThreadContainingMsgHdr(aMsgHdr)``

Return the view thread corresponding to aMsgHdr. If we're a cross-folder
view, then it would be the cross folder view thread, otherwise, the
db thread object.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgThread`

  view thread object for msg hdr.

addColumnHandler
----------------

``void addColumnHandler(aColumn, aHandler)``

Parameters
^^^^^^^^^^

* in AString aColumn
* in :doc:`nsIMsgCustomColumnHandler` aHandler

removeColumnHandler
-------------------

``void removeColumnHandler(aColumn)``

Parameters
^^^^^^^^^^

* in AString aColumn

getColumnHandler
----------------

``nsIMsgCustomColumnHandler getColumnHandler(aColumn)``

Parameters
^^^^^^^^^^

* in AString aColumn

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgCustomColumnHandler`

cellTextForColumn
-----------------

``AString cellTextForColumn(aRow, aColumnName)``

Scriptable accessor for the cell text for a column

@notes This does not work for custom columns yet.

Parameters
^^^^^^^^^^

* in long aRow
* in AString aColumnName

Return value
^^^^^^^^^^^^

* AString

  The cell text for the given row and column, if any.

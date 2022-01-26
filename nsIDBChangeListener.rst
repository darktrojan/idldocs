===================
nsIDBChangeListener
===================

`mailnews/db/msgdb/public/nsIDBChangeListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIDBChangeListener.idl>`_

These callbacks are provided to allow listeners to the message database
to update their status when changes occur.

Methods
=======

onHdrFlagsChanged
-----------------

``void onHdrFlagsChanged(aHdrChanged, aOldFlags, aNewFlags, aInstigator)``

Callback when message flags are changed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrChanged
* in unsigned long aOldFlags
* in unsigned long aNewFlags
* in :doc:`nsIDBChangeListener` aInstigator

onHdrDeleted
------------

``void onHdrDeleted(aHdrChanged, aParentKey, aFlags, aInstigator)``

Callback when message is marked as deleted.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrChanged
* in nsMsgKey aParentKey
* in long aFlags
* in :doc:`nsIDBChangeListener` aInstigator

onHdrAdded
----------

``void onHdrAdded(aHdrChanged, aParentKey, aFlags, aInstigator)``

Callback when message is added.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrChanged
* in nsMsgKey aParentKey
* in long aFlags
* in :doc:`nsIDBChangeListener` aInstigator

onParentChanged
---------------

``void onParentChanged(aKeyChanged, oldParent, newParent, aInstigator)``

Callback when message parent is changed. Parent is changed when message is deleted or moved.

Parameters
^^^^^^^^^^

* in nsMsgKey aKeyChanged
* in nsMsgKey oldParent
* in nsMsgKey newParent
* in :doc:`nsIDBChangeListener` aInstigator

onAnnouncerGoingAway
--------------------

``void onAnnouncerGoingAway(instigator)``

Callback when announcer is going away. This is good place to release strong pointers to announcer.

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeAnnouncer` instigator

onReadChanged
-------------

``void onReadChanged(aInstigator)``

Callback when read flag is changed.

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` aInstigator

onJunkScoreChanged
------------------

``void onJunkScoreChanged(aInstigator)``

Callback used in case when "junkscore" property is changed.

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` aInstigator

onHdrPropertyChanged
--------------------

``void onHdrPropertyChanged(aHdrToChange, property, aPreChange, aStatus, aInstigator)``

Callback used in the general case where any field may have changed.
OnHdrPropertyChanged is called twice per change. On the first call, aPreChange
is true, and aStatus is undefined. OnHdrPropertyChanged saves any required status in aStatus
(such as a filter match). The calling function stores the value of aStatus, changes the
header aHdrToChange, then calls OnHdrPropertyChanged again with aPreChange false. On this
second call, the stored value of aStatus is provided, so that any changes may be noted.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrToChange
* in AUTF8String property
* in boolean aPreChange
* inout uint32_t aStatus
* in :doc:`nsIDBChangeListener` aInstigator

onEvent
-------

``void onEvent(aDB, aEvent)``

Generic notification for extensibility. Common events should be documented
here so we have a hope of keeping the documentation up to date.
Current events are:
"DBOpened" - When a pending listener becomes real. This can happen when
the existing db is force closed and a new one opened. Only
registered pending listeners are notified.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDatabase` aDB
* in string aEvent

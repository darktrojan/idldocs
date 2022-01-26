====================
nsIDBChangeAnnouncer
====================

`mailnews/db/msgdb/public/nsIDBChangeAnnouncer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIDBChangeAnnouncer.idl>`_


Methods
=======

AddListener
-----------

``void AddListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` listener

RemoveListener
--------------

``void RemoveListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` listener

NotifyHdrChangeAll
------------------

``void NotifyHdrChangeAll(aHdrChanged, aOldFlags, aNewFlags, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrChanged
* in unsigned long aOldFlags
* in unsigned long aNewFlags
* in :doc:`nsIDBChangeListener` instigator

NotifyHdrAddedAll
-----------------

``void NotifyHdrAddedAll(aHdrAdded, parentKey, flags, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrAdded
* in nsMsgKey parentKey
* in long flags
* in :doc:`nsIDBChangeListener` instigator

NotifyHdrDeletedAll
-------------------

``void NotifyHdrDeletedAll(aHdrDeleted, parentKey, flags, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdrDeleted
* in nsMsgKey parentKey
* in long flags
* in :doc:`nsIDBChangeListener` instigator

NotifyParentChangedAll
----------------------

``void NotifyParentChangedAll(keyReparented, oldParent, newParent, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey keyReparented
* in nsMsgKey oldParent
* in nsMsgKey newParent
* in :doc:`nsIDBChangeListener` instigator

NotifyReadChanged
-----------------

``void NotifyReadChanged(instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` instigator

NotifyJunkScoreChanged
----------------------

``void NotifyJunkScoreChanged(aInstigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` aInstigator

NotifyAnnouncerGoingAway
------------------------

``void NotifyAnnouncerGoingAway()``

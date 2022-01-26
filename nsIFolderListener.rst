=================
nsIFolderListener
=================

`mailnews/base/public/nsIFolderListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIFolderListener.idl>`_

nsIFolderListener defines callbacks to handle various notifications
about changes in folders.
These listeners can be attached to individual folders, or they
can be registered globally, with nsIMsgMailSession.
These notifications originate from nsIMsgFolder implementations.
(nsIMsgFolder has corresponding methods for generating these
notifications).

Constants
=========

added
-----

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``1``


removed
-------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``2``


propertyChanged
---------------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``4``


intPropertyChanged
------------------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``8``


boolPropertyChanged
-------------------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``16``


unicharPropertyChanged
----------------------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``32``


propertyFlagChanged
-------------------

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``64``


event
-----

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``128``


all
---

**Type**: ``folderListenerNotifyFlagValue``

**Value**: ``4294967295``


Methods
=======

onFolderAdded
-------------

``void onFolderAdded(parent, child)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` parent
* in :doc:`nsIMsgFolder` child

onMessageAdded
--------------

``void onMessageAdded(parent, msg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` parent
* in :doc:`nsIMsgDBHdr` msg

onFolderRemoved
---------------

``void onFolderRemoved(parent, child)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` parent
* in :doc:`nsIMsgFolder` child

onMessageRemoved
----------------

``void onMessageRemoved(parent, msg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` parent
* in :doc:`nsIMsgDBHdr` msg

onFolderPropertyChanged
-----------------------

``void onFolderPropertyChanged(folder, property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in ACString property
* in AUTF8String oldValue
* in AUTF8String newValue

onFolderIntPropertyChanged
--------------------------

``void onFolderIntPropertyChanged(folder, property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in ACString property
* in long long oldValue
* in long long newValue

onFolderBoolPropertyChanged
---------------------------

``void onFolderBoolPropertyChanged(folder, property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in ACString property
* in boolean oldValue
* in boolean newValue

onFolderUnicharPropertyChanged
------------------------------

``void onFolderUnicharPropertyChanged(folder, property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in ACString property
* in AString oldValue
* in AString newValue

onFolderPropertyFlagChanged
---------------------------

``void onFolderPropertyFlagChanged(msg, property, oldFlag, newFlag)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg
* in ACString property
* in unsigned long oldFlag
* in unsigned long newFlag

onFolderEvent
-------------

``void onFolderEvent(folder, event)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in ACString event

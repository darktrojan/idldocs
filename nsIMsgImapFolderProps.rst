=====================
nsIMsgImapFolderProps
=====================

`mailnews/imap/public/nsIMsgImapMailFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIMsgImapMailFolder.idl>`_

nsIMsgImapFolderProps is a simple interface which allows the IMAP folder to
update some values that the folder props js code will use to update the
sharing and quota tabs in the folder properties.

Methods
=======

setFolderType
-------------

``void setFolderType(folderType)``

Parameters
^^^^^^^^^^

* in AString folderType

setFolderTypeDescription
------------------------

``void setFolderTypeDescription(folderTypeDescription)``

Parameters
^^^^^^^^^^

* in AString folderTypeDescription

setFolderPermissions
--------------------

``void setFolderPermissions(permissions)``

Parameters
^^^^^^^^^^

* in AString permissions

serverDoesntSupportACL
----------------------

``void serverDoesntSupportACL()``

showQuotaData
-------------

``void showQuotaData(showData)``

Toggles the display of quota information in the Quota tab of the folder properties.
If on, the quota root, usage, and percentage used are displayed.
If off, a status message is displayed. The status message can be set with setQuotaStatus().

Parameters
^^^^^^^^^^

* in boolean showData

setQuotaStatus
--------------

``void setQuotaStatus(folderQuotaStatus)``

Sets the status string displayed in the Quota tab of the folder properties if quota
information is not visible.

Parameters
^^^^^^^^^^

* in AString folderQuotaStatus

setQuotaData
------------

``void setQuotaData(quotaArray)``

Sets the quota data displayed in the folder properties Quota tab. An
array of quota items is passed in.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgQuota`> quotaArray

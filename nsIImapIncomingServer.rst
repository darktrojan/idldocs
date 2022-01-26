=====================
nsIImapIncomingServer
=====================

`mailnews/imap/public/nsIImapIncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapIncomingServer.idl>`_


Properties
==========

maximumConnectionsNumber
------------------------

``attribute long maximumConnectionsNumber``

forceSelect
-----------

``attribute ACString forceSelect``

timeOutLimits
-------------

``attribute long timeOutLimits``

adminUrl
--------

``attribute ACString adminUrl``

serverDirectory
---------------

``attribute ACString serverDirectory``

serverIDPref
------------

``attribute ACString serverIDPref``

cleanupInboxOnExit
------------------

``attribute boolean cleanupInboxOnExit``

deleteModel
-----------

``attribute nsMsgImapDeleteModel deleteModel``

dualUseFolders
--------------

``attribute boolean dualUseFolders``

personalNamespace
-----------------

``attribute ACString personalNamespace``

publicNamespace
---------------

``attribute ACString publicNamespace``

otherUsersNamespace
-------------------

``attribute ACString otherUsersNamespace``

offlineDownload
---------------

``attribute boolean offlineDownload``

overrideNamespaces
------------------

``attribute boolean overrideNamespaces``

usingSubscription
-----------------

``attribute boolean usingSubscription``

manageMailAccountUrl
--------------------

``attribute ACString manageMailAccountUrl``

fetchByChunks
-------------

``attribute boolean fetchByChunks``

mimePartsOnDemand
-----------------

``attribute boolean mimePartsOnDemand``

sendID
------

``attribute boolean sendID``

isAOLServer
-----------

``attribute boolean isAOLServer``

useIdle
-------

``attribute boolean useIdle``

checkAllFoldersForNew
---------------------

``attribute boolean checkAllFoldersForNew``

isGMailServer
-------------

``attribute boolean isGMailServer``

useCondStore
------------

``attribute boolean useCondStore``

See IMAP RFC 4551
*/

useCompressDeflate
------------------

``attribute boolean useCompressDeflate``

See IMAP RFC 4978

trashFolderName
---------------

``attribute AString trashFolderName``

This contains a folder path, for example INBOX/Trash. Note that the
account manager sets this attribute to the path of the trash folder the
user has chosen.

downloadBodiesOnGetNewMail
--------------------------

``attribute boolean downloadBodiesOnGetNewMail``

autoSyncOfflineStores
---------------------

``attribute boolean autoSyncOfflineStores``

autoSyncMaxAgeDays
------------------

``attribute long autoSyncMaxAgeDays``

allowUTF8Accept
---------------

``attribute boolean allowUTF8Accept``

See IMAP RFC 6855

doingLsub
---------

``attribute boolean doingLsub``

shuttingDown
------------

``attribute boolean shuttingDown``

utf8AcceptEnabled
-----------------

``attribute boolean utf8AcceptEnabled``

Methods
=======

GetImapConnectionAndLoadUrl
---------------------------

``void GetImapConnectionAndLoadUrl(aImapUrl, aConsumer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aImapUrl
* in :doc:`nsISupports` aConsumer

RemoveConnection
----------------

``void RemoveConnection(aImapConnection)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aImapConnection

ResetNamespaceReferences
------------------------

``void ResetNamespaceReferences()``

pseudoInterruptMsgLoad
----------------------

``void pseudoInterruptMsgLoad(aImapFolder, aMsgWindow, interrupted)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* out boolean interrupted

ResetConnection
---------------

``void ResetConnection(folderName)``

Parameters
^^^^^^^^^^

* in ACString folderName

CloseConnectionForFolder
------------------------

``void CloseConnectionForFolder(aMsgFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMsgFolder

reDiscoverAllFolders
--------------------

``void reDiscoverAllFolders()``

subscribeToFolder
-----------------

``nsIURI subscribeToFolder(name, subscribe)``

Parameters
^^^^^^^^^^

* in AString name
* in boolean subscribe

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

GetNewMessagesForNonInboxFolders
--------------------------------

``void GetNewMessagesForNonInboxFolders(aRootFolder, aWindow, forceAllFolders, performingBiff)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aRootFolder
* in :doc:`nsIMsgWindow` aWindow
* in boolean forceAllFolders
* in boolean performingBiff

getCapability
-------------

``void getCapability(capability)``

Parameters
^^^^^^^^^^

* out unsigned long long capability

PromptPassword
--------------

``AString PromptPassword(aWindow)``

Get the password from the nsIMsgIncomingServer. May prompt the user
if there's no password in the password manager or cached in the
server object.
@note NS_MSG_PASSWORD_PROMPT_CANCELLED is a success code that is returned
if the prompt was presented to the user but the user cancelled the
prompt.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow

Return value
^^^^^^^^^^^^

* AString

  Password string.

Throws
^^^^^^

* NS_ERROR_FAILURE  The password could not be obtained.

getUriWithNamespacePrefixIfNecessary
------------------------------------

``ACString getUriWithNamespacePrefixIfNecessary(namespaceType, originalUri)``

Parameters
^^^^^^^^^^

* in long namespaceType
* in AUTF8String originalUri

Return value
^^^^^^^^^^^^

* ACString

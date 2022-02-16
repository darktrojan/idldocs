=================
nsIImapServerSink
=================

`mailnews/imap/public/nsIImapServerSink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapServerSink.idl>`_

nsIImapServerSink is designed to be used as a proxy to the application's UI
thread from the running IMAP threads.

Properties
==========

userAuthenticated
-----------------

``attribute boolean userAuthenticated``

arbitraryHeaders
----------------

``readonly attribute ACString arbitraryHeaders``

showAttachmentsInline
---------------------

``readonly attribute boolean showAttachmentsInline``

loginUsername
-------------

``readonly attribute ACString loginUsername``

originalUsername
----------------

``readonly attribute ACString originalUsername``

serverKey
---------

``readonly attribute ACString serverKey``

serverPassword
--------------

``readonly attribute AString serverPassword``

serverShuttingDown
------------------

``readonly attribute boolean serverShuttingDown``

Methods
=======

possibleImapMailbox
-------------------

``boolean possibleImapMailbox(folderPath, hierarchyDelimiter, boxFlags)``

Check if the given folder path is a possible IMAP mailbox.

Parameters
^^^^^^^^^^

* in ACString folderPath
* in char hierarchyDelimiter
* in long boxFlags

Return value
^^^^^^^^^^^^

* boolean

  true if it's a new mailbox

folderNeedsACLInitialized
-------------------------

``boolean folderNeedsACLInitialized(folderPath)``

Parameters
^^^^^^^^^^

* in ACString folderPath

Return value
^^^^^^^^^^^^

* boolean

addFolderRights
---------------

``void addFolderRights(folderPath, userName, rights)``

Parameters
^^^^^^^^^^

* in ACString folderPath
* in ACString userName
* in ACString rights

refreshFolderRights
-------------------

``void refreshFolderRights(folderPath)``

Parameters
^^^^^^^^^^

* in ACString folderPath

discoveryDone
-------------

``void discoveryDone()``

onlineFolderDelete
------------------

``void onlineFolderDelete(folderName)``

Parameters
^^^^^^^^^^

* in ACString folderName

onlineFolderCreateFailed
------------------------

``void onlineFolderCreateFailed(aFolderName)``

Parameters
^^^^^^^^^^

* in ACString aFolderName

onlineFolderRename
------------------

``void onlineFolderRename(msgWindow, oldName, newName)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow
* in ACString oldName
* in ACString newName

folderIsNoSelect
----------------

``boolean folderIsNoSelect(folderName)``

Parameters
^^^^^^^^^^

* in ACString folderName

Return value
^^^^^^^^^^^^

* boolean

setFolderAdminURL
-----------------

``void setFolderAdminURL(folderName, adminUrl)``

Parameters
^^^^^^^^^^

* in ACString folderName
* in ACString adminUrl

folderVerifiedOnline
--------------------

``boolean folderVerifiedOnline(folderName)``

Parameters
^^^^^^^^^^

* in ACString folderName

Return value
^^^^^^^^^^^^

* boolean

setCapability
-------------

``void setCapability(capability)``

Parameters
^^^^^^^^^^

* in unsigned long long capability

setServerID
-----------

``void setServerID(aServerID)``

Parameters
^^^^^^^^^^

* in ACString aServerID

loadNextQueuedUrl
-----------------

``boolean loadNextQueuedUrl(protocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` protocol

Return value
^^^^^^^^^^^^

* boolean

prepareToRetryUrl
-----------------

``nsIImapMockChannel prepareToRetryUrl(imapUrl)``

Prepare to retry the given URL.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` imapUrl

Return value
^^^^^^^^^^^^

* :doc:`nsIImapMockChannel`

  channel to associate with the url. We return this because access
  to the channel should only happen on the ui thread.

suspendUrl
----------

``void suspendUrl(aImapUrl)``

Suspend the url. This puts it at the end of the queue. If the queue is
empty, the url will get resumed immediately. Currently, the plan is
do this when we have to download a lot of headers in chunks, though we
could find other uses for it.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aImapUrl

retryUrl
--------

``void retryUrl(imapUrl, channel)``

Retry the given URL.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` imapUrl
* in :doc:`nsIImapMockChannel` channel

abortQueuedUrls
---------------

``void abortQueuedUrls()``

If previous URL failed, this gives server chance to abort URLs with same
mock channel.

getImapStringByName
-------------------

``AString getImapStringByName(msgName)``

Parameters
^^^^^^^^^^

* in string msgName

Return value
^^^^^^^^^^^^

* AString

promptLoginFailed
-----------------

``int32_t promptLoginFailed(aMsgWindow)``

Alerts the user that the login to the IMAP server failed. Asks whether the
connection should: retry, cancel, or request a new password.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* int32_t

  The button pressed. 0 for retry, 1 for cancel,
  2 for enter a new password.

fEAlert
-------

``void fEAlert(aAlertString, aUrl)``

Alerts the user with the given string (FE = 'Front End').

Parameters
^^^^^^^^^^

* in AString aAlertString
* in :doc:`nsIMsgMailNewsUrl` aUrl

fEAlertWithName
---------------

``void fEAlertWithName(aMsgName, aUrl)``

Alerts the user with a localized string. It will attempt to fill in
the hostname into the string if necessary.

Parameters
^^^^^^^^^^

* in string aMsgName
* in :doc:`nsIMsgMailNewsUrl` aUrl

fEAlertFromServer
-----------------

``void fEAlertFromServer(aServerString, aUrl)``

Takes a response from the server and prepends it with IMAP_SERVER_SAID

Parameters
^^^^^^^^^^

* in ACString aServerString
* in :doc:`nsIMsgMailNewsUrl` aUrl

commitNamespaces
----------------

``void commitNamespaces()``

asyncGetPassword
----------------

``void asyncGetPassword(aProtocol, aNewPasswordRequested, aPassword)``

Returns a password via the out param, if we were able to prompt for one,
or had one stored.
If there is already a password prompt up, we return false, but we
ask the async prompt service to notify us when we can put up a prompt.
When that notification is received, we prompt the user and set the
password on the protocol object, and signal a monitor that the imap
thread should be waiting on.

rv is NS_MSG_PASSWORD_PROMPT_CANCELLED if the user cancels the
password prompt. That's not an exception, however.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in boolean aNewPasswordRequested
* out AString aPassword

setMailServerUrls
-----------------

``void setMailServerUrls(manageMailAccount, manageLists, manageFilters)``

Parameters
^^^^^^^^^^

* in ACString manageMailAccount
* in ACString manageLists
* in ACString manageFilters

UpdateTrySTARTTLSPref
---------------------

``void UpdateTrySTARTTLSPref(aSucceeded)``

Used by the imap thread when upgrading from the socketType
trySTARTTLS.

Parameters
^^^^^^^^^^

* in boolean aSucceeded

forgetPassword
--------------

``void forgetPassword()``

cramMD5Hash
-----------

``string cramMD5Hash(decodedChallenge, key)``

Parameters
^^^^^^^^^^

* in string decodedChallenge
* in string key

Return value
^^^^^^^^^^^^

* string

removeServerConnection
----------------------

``void removeServerConnection(aProtocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol

resetServerConnection
---------------------

``void resetServerConnection(aFolderName)``

Parameters
^^^^^^^^^^

* in ACString aFolderName

setServerDoingLsub
------------------

``void setServerDoingLsub(aDoingLsub)``

Parameters
^^^^^^^^^^

* in boolean aDoingLsub

SetServerForceSelect
--------------------

``void SetServerForceSelect(forceSelect)``

Parameters
^^^^^^^^^^

* in ACString forceSelect

setServerUtf8AcceptEnabled
--------------------------

``void setServerUtf8AcceptEnabled(aEnabled)``

Parameters
^^^^^^^^^^

* in boolean aEnabled

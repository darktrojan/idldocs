==========
nsIImapUrl
==========

`mailnews/imap/public/nsIImapUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapUrl.idl>`_


Constants
=========

ImapStatusNone
--------------

**Type**: ``long``

**Value**: ``0``

Current possible extra status values

ImapStatusFlagChangeFailed
--------------------------

**Type**: ``long``

**Value**: ``1``


ImapStatusFlagsNotSettable
--------------------------

**Type**: ``long``

**Value**: ``2``


nsImapAuthenticatedState
------------------------

**Type**: ``long``

**Value**: ``0``

@} */

nsImapSelectedState
-------------------

**Type**: ``long``

**Value**: ``1``


nsImapActionSendText
--------------------

**Type**: ``long``

**Value**: ``0``


nsImapTest
----------

**Type**: ``long``

**Value**: ``1``


nsImapCreateFolder
------------------

**Type**: ``long``

**Value**: ``5``


nsImapDeleteFolder
------------------

**Type**: ``long``

**Value**: ``6``


nsImapRenameFolder
------------------

**Type**: ``long``

**Value**: ``7``


nsImapMoveFolderHierarchy
-------------------------

**Type**: ``long``

**Value**: ``8``


nsImapLsubFolders
-----------------

**Type**: ``long``

**Value**: ``9``


nsImapGetMailAccountUrl
-----------------------

**Type**: ``long``

**Value**: ``10``


nsImapDiscoverChildrenUrl
-------------------------

**Type**: ``long``

**Value**: ``11``


nsImapDiscoverAllBoxesUrl
-------------------------

**Type**: ``long``

**Value**: ``13``


nsImapDiscoverAllAndSubscribedBoxesUrl
--------------------------------------

**Type**: ``long``

**Value**: ``14``


nsImapAppendMsgFromFile
-----------------------

**Type**: ``long``

**Value**: ``15``


nsImapSubscribe
---------------

**Type**: ``long``

**Value**: ``16``


nsImapUnsubscribe
-----------------

**Type**: ``long``

**Value**: ``17``


nsImapRefreshACL
----------------

**Type**: ``long``

**Value**: ``18``


nsImapRefreshAllACLs
--------------------

**Type**: ``long``

**Value**: ``19``


nsImapListFolder
----------------

**Type**: ``long``

**Value**: ``20``


nsImapUpgradeToSubscription
---------------------------

**Type**: ``long``

**Value**: ``21``


nsImapFolderStatus
------------------

**Type**: ``long``

**Value**: ``22``


nsImapRefreshFolderUrls
-----------------------

**Type**: ``long``

**Value**: ``23``


nsImapEnsureExistsFolder
------------------------

**Type**: ``long``

**Value**: ``24``


nsImapOfflineToOnlineCopy
-------------------------

**Type**: ``long``

**Value**: ``25``


nsImapOfflineToOnlineMove
-------------------------

**Type**: ``long``

**Value**: ``26``


nsImapVerifylogon
-----------------

**Type**: ``long``

**Value**: ``27``


nsImapSelectFolder
------------------

**Type**: ``long``

**Value**: ``268435458``


nsImapLiteSelectFolder
----------------------

**Type**: ``long``

**Value**: ``268435459``


nsImapExpungeFolder
-------------------

**Type**: ``long``

**Value**: ``268435460``


nsImapMsgFetch
--------------

**Type**: ``long``

**Value**: ``268435480``


nsImapMsgHeader
---------------

**Type**: ``long``

**Value**: ``268435481``


nsImapSearch
------------

**Type**: ``long``

**Value**: ``268435482``


nsImapDeleteMsg
---------------

**Type**: ``long``

**Value**: ``268435483``


nsImapDeleteAllMsgs
-------------------

**Type**: ``long``

**Value**: ``268435484``


nsImapAddMsgFlags
-----------------

**Type**: ``long``

**Value**: ``268435485``


nsImapSubtractMsgFlags
----------------------

**Type**: ``long``

**Value**: ``268435486``


nsImapSetMsgFlags
-----------------

**Type**: ``long``

**Value**: ``268435487``


nsImapOnlineCopy
----------------

**Type**: ``long``

**Value**: ``268435488``


nsImapOnlineMove
----------------

**Type**: ``long``

**Value**: ``268435489``


nsImapOnlineToOfflineCopy
-------------------------

**Type**: ``long``

**Value**: ``268435490``


nsImapOnlineToOfflineMove
-------------------------

**Type**: ``long``

**Value**: ``268435491``


nsImapMsgPreview
----------------

**Type**: ``long``

**Value**: ``268435492``


nsImapBiff
----------

**Type**: ``long``

**Value**: ``268435494``


nsImapSelectNoopFolder
----------------------

**Type**: ``long``

**Value**: ``268435495``


nsImapAppendDraftFromFile
-------------------------

**Type**: ``long``

**Value**: ``268435496``


nsImapUidExpunge
----------------

**Type**: ``long``

**Value**: ``268435497``


nsImapSaveMessageToDisk
-----------------------

**Type**: ``long``

**Value**: ``268435504``


nsImapOpenMimePart
------------------

**Type**: ``long``

**Value**: ``268435505``


nsImapMsgDownloadForOffline
---------------------------

**Type**: ``long``

**Value**: ``268435506``


nsImapDeleteFolderAndMsgs
-------------------------

**Type**: ``long``

**Value**: ``268435507``


nsImapUserDefinedMsgCommand
---------------------------

**Type**: ``long``

**Value**: ``268435508``


nsImapUserDefinedFetchAttribute
-------------------------------

**Type**: ``long``

**Value**: ``268435509``


nsImapMsgFetchPeek
------------------

**Type**: ``long``

**Value**: ``268435510``


nsImapMsgStoreCustomKeywords
----------------------------

**Type**: ``long``

**Value**: ``268435511``


DEFAULT_IMAP_PORT
-----------------

**Type**: ``int32_t``

**Value**: ``143``


DEFAULT_IMAPS_PORT
------------------

**Type**: ``int32_t``

**Value**: ``993``


Properties
==========

imapMailFolderSink
------------------

``attribute nsIImapMailFolderSink imapMailFolderSink``

imapMessageSink
---------------

``attribute nsIImapMessageSink imapMessageSink``

imapServerSink
--------------

``attribute nsIImapServerSink imapServerSink``

imapAction
----------

``attribute nsImapAction imapAction``

requiredImapState
-----------------

``readonly attribute nsImapState requiredImapState``

imapPartToFetch
---------------

``readonly attribute string imapPartToFetch``

customAttributeToFetch
----------------------

``readonly attribute ACString customAttributeToFetch``

customAttributeResult
---------------------

``attribute ACString customAttributeResult``

command
-------

``readonly attribute ACString command``

customCommandResult
-------------------

``attribute ACString customCommandResult``

customAddFlags
--------------

``readonly attribute ACString customAddFlags``

customSubtractFlags
-------------------

``readonly attribute ACString customSubtractFlags``

listOfMessageIds
----------------

``readonly attribute ACString listOfMessageIds``

msgFlags
--------

``readonly attribute imapMessageFlagsType msgFlags``

numBytesToFetch
---------------

``readonly attribute long numBytesToFetch``

onlineSubDirSeparator
---------------------

``attribute char onlineSubDirSeparator``

allowContentChange
------------------

``attribute boolean allowContentChange``

mimePartSelectorDetected
------------------------

``attribute boolean mimePartSelectorDetected``

contentModified
---------------

``attribute nsImapContentModifiedType contentModified``

fetchPartsOnDemand
------------------

``attribute boolean fetchPartsOnDemand``

msgLoadingFromCache
-------------------

``attribute boolean msgLoadingFromCache``

externalLinkUrl
---------------

``attribute boolean externalLinkUrl``

validUrl
--------

``attribute boolean validUrl``

copyState
---------

``attribute nsISupports copyState``

copyState is used by some IMAP copy operations. The exact type stashed
here depends on the operation being performed. For online move/copy,
it'll be an nsImapMailCopyState (private to nsImapMailFolder). For
other operations it might be (say), an nsIStreamListener.

msgFile
-------

``attribute nsIFile msgFile``

mockChannel
-----------

``attribute nsIImapMockChannel mockChannel``

storeResultsOffline
-------------------

``attribute boolean storeResultsOffline``

Set to true if we should store the msg(s) for offline use if we can,
e.g., we're fetching a message and the folder is configured for offline
use and we're not doing mime parts on demand.

storeOfflineOnFallback
----------------------

``attribute boolean storeOfflineOnFallback``

If we fallback from fetching by parts to fetching the whole message,
because all the parts were inline, this tells us we should store
the message offline.

localFetchOnly
--------------

``attribute boolean localFetchOnly``

This attribute defaults to false, but if we only want to use the offline
cache (disk, memory, or offline store) to fetch the message, then we set
this to true. Currently, nsIMsgMessageService.streamMessage does this.

rerunningUrl
------------

``attribute boolean rerunningUrl``

moreHeadersToDownload
---------------------

``attribute boolean moreHeadersToDownload``

Do we have more headers to download? This is set when we decide to
download newest headers first, followed by older headers in a subsequent
run of the url, which allows other urls to run against the folder in the
meantime.

extraStatus
-----------

``attribute long extraStatus``

@{
This is used to tell the runner of the url more about the status of
the command, beyond whether it was successful or not. For example,
subtracting flags from a UID that doesn't exist isn't an error
(the server returns OK), but the backend code may want to know about it.

Methods
=======

allocateCanonicalPath
---------------------

``void allocateCanonicalPath(aServerPath, aOnlineDelimiter, aAllocatedPath)``

Parameters
^^^^^^^^^^

* in string aServerPath
* in char aOnlineDelimiter
* out string aAllocatedPath

allocateServerPath
------------------

``void allocateServerPath(aCanonicalPath, aOnlineDelimiter, aAllocatedPath)``

Parameters
^^^^^^^^^^

* in string aCanonicalPath
* in char aOnlineDelimiter
* out string aAllocatedPath

createServerSourceFolderPathString
----------------------------------

``string createServerSourceFolderPathString()``

Return value
^^^^^^^^^^^^

* string

createCanonicalSourceFolderPathString
-------------------------------------

``string createCanonicalSourceFolderPathString()``

Return value
^^^^^^^^^^^^

* string

createServerDestinationFolderPathString
---------------------------------------

``string createServerDestinationFolderPathString()``

Return value
^^^^^^^^^^^^

* string

addOnlineDirectoryIfNecessary
-----------------------------

``string addOnlineDirectoryIfNecessary(onlineMailboxName)``

Parameters
^^^^^^^^^^

* in string onlineMailboxName

Return value
^^^^^^^^^^^^

* string

createSearchCriteriaString
--------------------------

``void createSearchCriteriaString(aResult)``

Parameters
^^^^^^^^^^

* out string aResult

messageIdsAreUids
-----------------

``boolean messageIdsAreUids()``

Return value
^^^^^^^^^^^^

* boolean

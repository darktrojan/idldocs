============
nsIMessenger
============

`mailnews/base/public/nsIMessenger.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMessenger.idl>`_


Constants
=========

eUnknown
--------

**Type**: ``long``

**Value**: ``0``


eDeleteMsg
----------

**Type**: ``long``

**Value**: ``1``


eMoveMsg
--------

**Type**: ``long``

**Value**: ``2``


eCopyMsg
--------

**Type**: ``long``

**Value**: ``3``


eMarkAllMsg
-----------

**Type**: ``long``

**Value**: ``4``


Properties
==========

transactionManager
------------------

``readonly attribute nsITransactionManager transactionManager``

lastDisplayedMessageUri
-----------------------

``readonly attribute AUTF8String lastDisplayedMessageUri``

navigatePos
-----------

``attribute long navigatePos``

Methods
=======

setWindow
---------

``void setWindow(ptr, msgWindow)``

Parameters
^^^^^^^^^^

* in mozIDOMWindowProxy ptr
* in :doc:`nsIMsgWindow` msgWindow

addMsgUrlToNavigateHistory
--------------------------

``void addMsgUrlToNavigateHistory(aURL)``

Parameters
^^^^^^^^^^

* in AUTF8String aURL

abortPendingOpenURL
-------------------

``void abortPendingOpenURL()``

Prevent any pending message load from occurring.

openURL
-------

``void openURL(aURL)``

Changes the message pane to the parent process if necessary, and loads
a message (aURL) in it. This may not happen synchronously.

Parameters
^^^^^^^^^^

* in AUTF8String aURL

loadURL
-------

``void loadURL(ptr, aURL)``

Load a custom message by url, e.g load a attachment as a email

Parameters
^^^^^^^^^^

* in mozIDOMWindowProxy ptr
* in AUTF8String aURL

launchExternalURL
-----------------

``void launchExternalURL(aURL)``

Parameters
^^^^^^^^^^

* in AUTF8String aURL

canUndo
-------

``boolean canUndo()``

Return value
^^^^^^^^^^^^

* boolean

canRedo
-------

``boolean canRedo()``

Return value
^^^^^^^^^^^^

* boolean

getUndoTransactionType
----------------------

``unsigned long getUndoTransactionType()``

Return value
^^^^^^^^^^^^

* unsigned long

getRedoTransactionType
----------------------

``unsigned long getRedoTransactionType()``

Return value
^^^^^^^^^^^^

* unsigned long

undo
----

``void undo(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

redo
----

``void redo(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

forceDetectDocumentCharset
--------------------------

``void forceDetectDocumentCharset()``

saveAs
------

``void saveAs(aURI, aAsFile, aIdentity, aMsgFilename, aBypassFilePicker)``

Saves a given message to a file or template.

Parameters
^^^^^^^^^^

* in AUTF8String aURI
* in boolean aAsFile
* in :doc:`nsIMsgIdentity` aIdentity
* in AString aMsgFilename
* in boolean aBypassFilePicker

saveMessages
------------

``void saveMessages(filenameArray, messageUriArray)``

Save the given messages as files in a folder - the user will be prompted
for which folder to use.

Parameters
^^^^^^^^^^

* in Array<AString> filenameArray
* in Array<AUTF8String> messageUriArray

openAttachment
--------------

``void openAttachment(contentType, url, displayName, messageUri, isExternalAttachment)``

Parameters
^^^^^^^^^^

* in AUTF8String contentType
* in AUTF8String url
* in AUTF8String displayName
* in AUTF8String messageUri
* in boolean isExternalAttachment

saveAttachment
--------------

``void saveAttachment(contentType, url, displayName, messageUri, isExternalAttachment)``

Parameters
^^^^^^^^^^

* in AUTF8String contentType
* in AUTF8String url
* in AUTF8String displayName
* in AUTF8String messageUri
* in boolean isExternalAttachment

saveAllAttachments
------------------

``void saveAllAttachments(contentTypeArray, urlArray, displayNameArray, messageUriArray)``

Parameters
^^^^^^^^^^

* in Array<AUTF8String> contentTypeArray
* in Array<AUTF8String> urlArray
* in Array<AUTF8String> displayNameArray
* in Array<AUTF8String> messageUriArray

saveAttachmentToFile
--------------------

``void saveAttachmentToFile(aFile, aUrl, aMessageUri, aContentType, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in AUTF8String aUrl
* in AUTF8String aMessageUri
* in AUTF8String aContentType
* in :doc:`nsIUrlListener` aListener

detachAttachmentsWOPrompts
--------------------------

``void detachAttachmentsWOPrompts(aDestFolder, aContentTypeArray, aUrlArray, aDisplayNameArray, aMessageUriArray, aListener)``

For a single message and attachments, save these attachments to a file, and
remove from the message. No warning windows will appear, so this is
suitable for use in test and filtering.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aDestFolder
* in Array<AUTF8String> aContentTypeArray
* in Array<AUTF8String> aUrlArray
* in Array<AUTF8String> aDisplayNameArray
* in Array<AUTF8String> aMessageUriArray
* in :doc:`nsIUrlListener` aListener

detachAttachment
----------------

``void detachAttachment(contentType, url, displayName, messageUri, saveFirst, withoutWarning)``

Parameters
^^^^^^^^^^

* in AUTF8String contentType
* in AUTF8String url
* in AUTF8String displayName
* in AUTF8String messageUri
* in boolean saveFirst
* in boolean withoutWarning

detachAllAttachments
--------------------

``void detachAllAttachments(contentTypeArray, urlArray, displayNameArray, messageUriArray, saveFirst, withoutWarning)``

Parameters
^^^^^^^^^^

* in Array<AUTF8String> contentTypeArray
* in Array<AUTF8String> urlArray
* in Array<AUTF8String> displayNameArray
* in Array<AUTF8String> messageUriArray
* in boolean saveFirst
* in boolean withoutWarning

saveAttachmentToFolder
----------------------

``nsIFile saveAttachmentToFolder(contentType, url, displayName, messageUri, aDestFolder)``

Parameters
^^^^^^^^^^

* in AUTF8String contentType
* in AUTF8String url
* in AUTF8String displayName
* in AUTF8String messageUri
* in :doc:`nsIFile` aDestFolder

Return value
^^^^^^^^^^^^

* :doc:`nsIFile`

messageServiceFromURI
---------------------

``nsIMsgMessageService messageServiceFromURI(aUri)``

Parameters
^^^^^^^^^^

* in AUTF8String aUri

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgMessageService`

msgHdrFromURI
-------------

``nsIMsgDBHdr msgHdrFromURI(aUri)``

Parameters
^^^^^^^^^^

* in AUTF8String aUri

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

getMsgUriAtNavigatePos
----------------------

``AUTF8String getMsgUriAtNavigatePos(aPos)``

Parameters
^^^^^^^^^^

* in long aPos

Return value
^^^^^^^^^^^^

* AUTF8String

getFolderUriAtNavigatePos
-------------------------

``AUTF8String getFolderUriAtNavigatePos(aPos)``

Parameters
^^^^^^^^^^

* in long aPos

Return value
^^^^^^^^^^^^

* AUTF8String

getNavigateHistory
------------------

``Array<AUTF8String> getNavigateHistory()``

Fetch the message navigation history.

Return value
^^^^^^^^^^^^

* Array<AUTF8String>

  An array containing two URIs for each history position.
  First msgURI, then folderURI. So the array will be
  twice as long as the number of history positions.

formatFileSize
--------------

``AString formatFileSize(aPos, aUseKB)``

Parameters
^^^^^^^^^^

* in unsigned long long aPos
* in boolean aUseKB

Return value
^^^^^^^^^^^^

* AString

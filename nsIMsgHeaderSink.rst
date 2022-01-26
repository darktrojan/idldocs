================
nsIMsgHeaderSink
================

`mailnews/mime/public/nsIMimeMiscStatus.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeMiscStatus.idl>`_


Properties
==========

securityInfo
------------

``attribute nsISupports securityInfo``

dummyMsgHeader
--------------

``readonly attribute nsIMsgDBHdr dummyMsgHeader``

properties
----------

``readonly attribute nsIWritablePropertyBag2 properties``

Methods
=======

processHeaders
--------------

``void processHeaders(aHeaderNames, aHeaderValues, dontCollectAddress)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUTF8StringEnumerator` aHeaderNames
* in :doc:`nsIUTF8StringEnumerator` aHeaderValues
* in boolean dontCollectAddress

handleAttachment
----------------

``void handleAttachment(contentType, url, displayName, uri, aNotDownloaded)``

Parameters
^^^^^^^^^^

* in string contentType
* in AUTF8String url
* in wstring displayName
* in AUTF8String uri
* in boolean aNotDownloaded

addAttachmentField
------------------

``void addAttachmentField(field, value)``

Add a metadata field to the current attachment, e.g. "X-Mozilla-PartSize".

Parameters
^^^^^^^^^^

* in string field
* in string value

onEndAllAttachments
-------------------

``void onEndAllAttachments()``

onEndMsgHeaders
---------------

``void onEndMsgHeaders(url)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` url

onEndMsgDownload
----------------

``void onEndMsgDownload(url)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` url

onMsgHasRemoteContent
---------------------

``void onMsgHasRemoteContent(aMsgHdr, aContentURI, aCanOverride)``

onMsgHasRemoteContent is called each time content policy encounters remote
content that it will block from loading.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in :doc:`nsIURI` aContentURI
* in boolean aCanOverride

resetProperties
---------------

``void resetProperties()``

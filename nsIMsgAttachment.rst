================
nsIMsgAttachment
================

`mailnews/compose/public/nsIMsgAttachment.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgAttachment.idl>`_


Properties
==========

name
----

``attribute AString name``

name attribute

@Attachment real name, will be sent with the attachment's header.
@If no name has been provided, a name will be generated using the url.

url
---

``attribute AUTF8String url``

url attribute

@specify where the attachment live (localy or remotely)

urlCharset
----------

``attribute ACString urlCharset``

urlCharset attribute

@specify the Charset of url  (used to convert url to Unicode after
unescaping)

temporary
---------

``attribute boolean temporary``

temporary attribute

@If set to true, the file pointed by the url will be destroyed when this object is destroyed.
@This is only for local attachment.

sendViaCloud
------------

``attribute boolean sendViaCloud``

Are we storing this attachment via a cloud provider and linking to it?

cloudFileAccountKey
-------------------

``attribute ACString cloudFileAccountKey``

Cloud provider account key for this attachment, if any.

htmlAnnotation
--------------

``attribute AString htmlAnnotation``

This allows the compose front end code to put whatever html annotation
it wants for the cloud part, e.g., with expiration time, etc.

contentLocation
---------------

``attribute ACString contentLocation``

contentLocation attribute

@Specify the origin url of the attachment, used normally when attaching
a locally saved html document, but also used for cloud files.

contentType
-----------

``attribute string contentType``

contentType attribute

@Specify the content-type of the attachment, this does not include extra content-type parameters. If
@you need to specify extra information, use contentTypeParam, charset, macType or macCreator.
@If omitted, it will be determined base on either the name, the url or the content of the file.

contentTypeParam
----------------

``attribute string contentTypeParam``

contentTypeParam attribute

@Specify the any content-type parameter (other than the content-type itself, charset, macType or macCreator).
@It will be added to the content-type during the send/save operation.

contentId
---------

``attribute AUTF8String contentId``

Content-ID for embedded attachments inside a multipart/related container.

charset
-------

``attribute string charset``

charset attribute

@Specify the charset of the attachment. It will be added to the content-type during the
@send/save operation
@If omitted, will be determined automatically (if possible).

size
----

``attribute int64_t size``

size attribute

@Specify the size of the attachment.

macType
-------

``attribute string macType``

macType attribute

@Specify the Mac file type of the attachment. It will be added to the content-type during the
@send/save operation
@If omitted, will be determined automatically on Macintosh OS.

macCreator
----------

``attribute string macCreator``

macCreator attribute

@Specify the Mac file creator of the attachment. It will be added to the content-type during the
@send/save operation
@If omitted, will be determined automatically on Macintosh OS.

Methods
=======

equalsUrl
---------

``boolean equalsUrl(attachment)``

equalsUrl
@ determines if both attachments have the same url.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgAttachment` attachment

Return value
^^^^^^^^^^^^

* boolean

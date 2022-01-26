================
nsIMsgCompFields
================

`mailnews/compose/public/nsIMsgCompFields.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgCompFields.idl>`_

A collection of headers and other attributes for building a mail message.

Properties
==========

from
----

``attribute AString from``

replyTo
-------

``attribute AString replyTo``

to
--

``attribute AString to``

cc
--

``attribute AString cc``

bcc
---

``attribute AString bcc``

hasRecipients
-------------

``readonly attribute bool hasRecipients``

fcc
---

``attribute AString fcc``

fcc2
----

``attribute AString fcc2``

newsgroups
----------

``attribute AString newsgroups``

newspostUrl
-----------

``attribute string newspostUrl``

followupTo
----------

``attribute AString followupTo``

subject
-------

``attribute AString subject``

organization
------------

``attribute AString organization``

references
----------

``attribute string references``

priority
--------

``attribute string priority``

messageId
---------

``attribute string messageId``

templateName
------------

``attribute AString templateName``

draftId
-------

``attribute AUTF8String draftId``

templateId
----------

``attribute AUTF8String templateId``

returnReceipt
-------------

``attribute boolean returnReceipt``

receiptHeaderType
-----------------

``attribute long receiptHeaderType``

DSN
---

``attribute boolean DSN``

attachVCard
-----------

``attribute boolean attachVCard``

forcePlainText
--------------

``attribute boolean forcePlainText``

useMultipartAlternative
-----------------------

``attribute boolean useMultipartAlternative``

bodyIsAsciiOnly
---------------

``attribute boolean bodyIsAsciiOnly``

forceMsgEncoding
----------------

``attribute boolean forceMsgEncoding``

attachmentReminder
------------------

``attribute boolean attachmentReminder``

deliveryFormat
--------------

``attribute long deliveryFormat``

contentLanguage
---------------

``attribute string contentLanguage``

creatorIdentityKey
------------------

``attribute string creatorIdentityKey``

body
----

``attribute AString body``

Beware that when setting this property, your body must be properly wrapped,
and the line endings must match MSG_LINEBREAK, namely "\r\n" on Windows
and "\n" on Linux and OSX.

attachments
-----------

``readonly attribute Array<nsIMsgAttachment> attachments``

needToCheckCharset
------------------

``attribute boolean needToCheckCharset``

Indicates whether we need to check if the current |DocumentCharset|
can represent all the characters in the message body. It should be
initialized to true and set to false when 'Send Anyway' is selected
by a user. (bug 249530)

composeSecure
-------------

``attribute nsIMsgComposeSecure composeSecure``

Object implementing encryption/signing functionality (e.g. S/MIME, PGP/MIME)

Methods
=======

addAttachment
-------------

``void addAttachment(attachment)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgAttachment` attachment

removeAttachment
----------------

``void removeAttachment(attachment)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgAttachment` attachment

removeAttachments
-----------------

``void removeAttachments()``

splitRecipients
---------------

``Array<AString> splitRecipients(aRecipients, aEmailAddressOnly)``

This function will split the recipients into an array.

Parameters
^^^^^^^^^^

* in AString aRecipients
* in boolean aEmailAddressOnly

Return value
^^^^^^^^^^^^

* Array<AString>

  An array of the recipients.

ConvertBodyToPlainText
----------------------

``void ConvertBodyToPlainText()``

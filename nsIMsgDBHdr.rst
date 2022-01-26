===========
nsIMsgDBHdr
===========

`mailnews/base/public/nsIMsgHdr.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgHdr.idl>`_


Properties
==========

isRead
------

``readonly attribute boolean isRead``

isFlagged
---------

``readonly attribute boolean isFlagged``

isKilled
--------

``readonly attribute boolean isKilled``

priority
--------

``attribute nsMsgPriorityValue priority``

flags
-----

``attribute unsigned long flags``

threadId
--------

``attribute nsMsgKey threadId``

messageKey
----------

``attribute nsMsgKey messageKey``

threadParent
------------

``attribute nsMsgKey threadParent``

messageSize
-----------

``attribute unsigned long messageSize``

lineCount
---------

``attribute unsigned long lineCount``

statusOffset
------------

``attribute unsigned long statusOffset``

messageOffset
-------------

``attribute unsigned long long messageOffset``

The offset into the local folder/offline store of the message. This
will be pluggable store-dependent, e.g., for mail dir it should
always be 0.

offlineMessageSize
------------------

``attribute unsigned long offlineMessageSize``

date
----

``attribute PRTime date``

dateInSeconds
-------------

``readonly attribute unsigned long dateInSeconds``

messageId
---------

``attribute string messageId``

ccList
------

``attribute string ccList``

bccList
-------

``attribute string bccList``

author
------

``attribute string author``

subject
-------

``attribute string subject``

recipients
----------

``attribute string recipients``

numReferences
-------------

``readonly attribute unsigned short numReferences``

mime2DecodedAuthor
------------------

``readonly attribute AString mime2DecodedAuthor``

mime2DecodedSubject
-------------------

``readonly attribute AString mime2DecodedSubject``

mime2DecodedRecipients
----------------------

``readonly attribute AString mime2DecodedRecipients``

Charset
-------

``attribute string Charset``

effectiveCharset
----------------

``readonly attribute ACString effectiveCharset``

Returns the effective character set for the message (@ref Charset).
If there is no specific set defined for the message or the
characterSetOverride option is turned on for the folder it will return
the effective character set of the folder instead.

label
-----

``attribute nsMsgLabelValue label``

accountKey
----------

``attribute string accountKey``

folder
------

``readonly attribute nsIMsgFolder folder``

propertyEnumerator
------------------

``readonly attribute nsIUTF8StringEnumerator propertyEnumerator``

Methods
=======

getProperty
-----------

``AString getProperty(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* AString

setProperty
-----------

``void setProperty(propertyName, propertyStr)``

Parameters
^^^^^^^^^^

* in string propertyName
* in AString propertyStr

setStringProperty
-----------------

``void setStringProperty(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in string propertyValue

getStringProperty
-----------------

``string getStringProperty(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* string

getUint32Property
-----------------

``unsigned long getUint32Property(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* unsigned long

setUint32Property
-----------------

``void setUint32Property(propertyName, propertyVal)``

Parameters
^^^^^^^^^^

* in string propertyName
* in unsigned long propertyVal

markRead
--------

``void markRead(read)``

Parameters
^^^^^^^^^^

* in boolean read

markFlagged
-----------

``void markFlagged(flagged)``

Parameters
^^^^^^^^^^

* in boolean flagged

markHasAttachments
------------------

``void markHasAttachments(hasAttachments)``

Parameters
^^^^^^^^^^

* in boolean hasAttachments

setPriorityString
-----------------

``void setPriorityString(priority)``

Parameters
^^^^^^^^^^

* in string priority

OrFlags
-------

``unsigned long OrFlags(flags)``

Parameters
^^^^^^^^^^

* in unsigned long flags

Return value
^^^^^^^^^^^^

* unsigned long

AndFlags
--------

``unsigned long AndFlags(flags)``

Parameters
^^^^^^^^^^

* in unsigned long flags

Return value
^^^^^^^^^^^^

* unsigned long

setReferences
-------------

``void setReferences(references)``

Parameters
^^^^^^^^^^

* in string references

getStringReference
------------------

``ACString getStringReference(refNum)``

Parameters
^^^^^^^^^^

* in long refNum

Return value
^^^^^^^^^^^^

* ACString

getAuthorCollationKey
---------------------

``Array<octet> getAuthorCollationKey()``

Return value
^^^^^^^^^^^^

* Array<octet>

getSubjectCollationKey
----------------------

``Array<octet> getSubjectCollationKey()``

Return value
^^^^^^^^^^^^

* Array<octet>

getRecipientsCollationKey
-------------------------

``Array<octet> getRecipientsCollationKey()``

Return value
^^^^^^^^^^^^

* Array<octet>

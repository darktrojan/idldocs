================
nsIMsgSearchTerm
================

`mailnews/search/public/nsIMsgSearchTerm.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchTerm.idl>`_


Properties
==========

attrib
------

``attribute nsMsgSearchAttribValue attrib``

op
--

``attribute nsMsgSearchOpValue op``

value
-----

``attribute nsIMsgSearchValue value``

booleanAnd
----------

``attribute boolean booleanAnd``

arbitraryHeader
---------------

``attribute ACString arbitraryHeader``

hdrProperty
-----------

``attribute ACString hdrProperty``

Not to be confused with arbitraryHeader, which is a header in the
rfc822 message. This is a property of the nsIMsgDBHdr, and may have
nothing to do the message headers, e.g., gloda-id.
value.str will be compared with nsIMsgHdr::GetProperty(hdrProperty).

customId
--------

``attribute ACString customId``

beginsGrouping
--------------

``attribute boolean beginsGrouping``

endsGrouping
------------

``attribute boolean endsGrouping``

matchAllBeforeDeciding
----------------------

``readonly attribute boolean matchAllBeforeDeciding``

termAsString
------------

``readonly attribute ACString termAsString``

matchAll
--------

``attribute boolean matchAll``

Methods
=======

matchRfc822String
-----------------

``boolean matchRfc822String(aString, charset)``

Match the value against one of the emails found in the incoming
2047-encoded string.

Parameters
^^^^^^^^^^

* in ACString aString
* in string charset

Return value
^^^^^^^^^^^^

* boolean

matchRfc2047String
------------------

``boolean matchRfc2047String(aString, charset, charsetOverride)``

Match the current header value against the incoming 2047-encoded string.

This method will first apply the nsIMimeConverter decoding to the string
(using the supplied parameters) and will then match the value against the
decoded result.

Parameters
^^^^^^^^^^

* in ACString aString
* in string charset
* in boolean charsetOverride

Return value
^^^^^^^^^^^^

* boolean

matchDate
---------

``boolean matchDate(aTime)``

Parameters
^^^^^^^^^^

* in PRTime aTime

Return value
^^^^^^^^^^^^

* boolean

matchStatus
-----------

``boolean matchStatus(aStatus)``

Parameters
^^^^^^^^^^

* in unsigned long aStatus

Return value
^^^^^^^^^^^^

* boolean

matchPriority
-------------

``boolean matchPriority(priority)``

Parameters
^^^^^^^^^^

* in nsMsgPriorityValue priority

Return value
^^^^^^^^^^^^

* boolean

matchAge
--------

``boolean matchAge(days)``

Parameters
^^^^^^^^^^

* in PRTime days

Return value
^^^^^^^^^^^^

* boolean

matchSize
---------

``boolean matchSize(size)``

Parameters
^^^^^^^^^^

* in unsigned long size

Return value
^^^^^^^^^^^^

* boolean

matchLabel
----------

``boolean matchLabel(aLabelValue)``

Parameters
^^^^^^^^^^

* in nsMsgLabelValue aLabelValue

Return value
^^^^^^^^^^^^

* boolean

matchJunkStatus
---------------

``boolean matchJunkStatus(aJunkScore)``

Parameters
^^^^^^^^^^

* in string aJunkScore

Return value
^^^^^^^^^^^^

* boolean

matchJunkPercent
----------------

``boolean matchJunkPercent(aJunkPercent)``

Parameters
^^^^^^^^^^

* in unsigned long aJunkPercent

Return value
^^^^^^^^^^^^

* boolean

matchJunkScoreOrigin
--------------------

``boolean matchJunkScoreOrigin(aJunkScoreOrigin)``

Parameters
^^^^^^^^^^

* in string aJunkScoreOrigin

Return value
^^^^^^^^^^^^

* boolean

matchBody
---------

``boolean matchBody(aScopeTerm, aOffset, aLength, aCharset, aMsg, aDb)``

Test if the body of the passed in message matches "this" search term.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchScopeTerm` aScopeTerm
* in unsigned long long aOffset
* in unsigned long aLength
* in string aCharset
* in :doc:`nsIMsgDBHdr` aMsg
* in :doc:`nsIMsgDatabase` aDb

Return value
^^^^^^^^^^^^

* boolean

matchArbitraryHeader
--------------------

``boolean matchArbitraryHeader(aScopeTerm, aLength, aCharset, aCharsetOverride, aMsg, aDb, aHeaders, aForFilters)``

Test if the arbitrary header specified by this search term
matches the corresponding header in the passed in message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchScopeTerm` aScopeTerm
* in unsigned long aLength
* in string aCharset
* in boolean aCharsetOverride
* in :doc:`nsIMsgDBHdr` aMsg
* in :doc:`nsIMsgDatabase` aDb
* in ACString aHeaders
* in boolean aForFilters

Return value
^^^^^^^^^^^^

* boolean

matchHdrProperty
----------------

``boolean matchHdrProperty(msg)``

Compares value.str with nsIMsgHdr::GetProperty(hdrProperty).

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

Return value
^^^^^^^^^^^^

* boolean

  true if msg matches property, false otherwise.

matchUint32HdrProperty
----------------------

``boolean matchUint32HdrProperty(msg)``

Compares value.status with nsIMsgHdr::GetUint32Property(hdrProperty).

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

Return value
^^^^^^^^^^^^

* boolean

  true if msg matches property, false otherwise.

matchFolderFlag
---------------

``boolean matchFolderFlag(msg)``

Compares value.status with the folder flags of the msg's folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

Return value
^^^^^^^^^^^^

* boolean

  true if folder's flags match value.status, false otherwise.

matchKeyword
------------

``boolean matchKeyword(keyword)``

Parameters
^^^^^^^^^^

* in ACString keyword

Return value
^^^^^^^^^^^^

* boolean

matchCustom
-----------

``boolean matchCustom(msg)``

Does the message match the custom search term?

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

  message database object representing the message

Return value
^^^^^^^^^^^^

* boolean

  true if message matches

getAttributeFromString
----------------------

``nsMsgSearchAttribValue getAttributeFromString(aAttribName)``

Returns a nsMsgSearchAttribValue value corresponding to a field string from
the nsMsgSearchTerm.cpp::SearchAttribEntryTable table.
Does not handle custom attributes yet.

Parameters
^^^^^^^^^^

* in string aAttribName

Return value
^^^^^^^^^^^^

* nsMsgSearchAttribValue

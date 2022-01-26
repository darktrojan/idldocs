=================
nsMsgSearchAttrib
=================

`mailnews/search/public/nsMsgSearchCore.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsMsgSearchCore.idl>`_

Definitions of search attribute types. The numerical order
from here will also be used to determine the order that the
attributes display in the filter editor.

Constants
=========

Custom
------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``-2``


Default
-------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``-1``


Subject
-------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``0``


Sender
------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``1``


Body
----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``2``


Date
----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``3``


Priority
--------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``4``


MsgStatus
---------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``5``


To
--

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``6``


CC
--

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``7``


ToOrCC
------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``8``


AllAddresses
------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``9``


Location
--------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``10``


MessageKey
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``11``


AgeInDays
---------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``12``


FolderInfo
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``13``


Size
----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``14``


AnyText
-------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``15``


Keywords
--------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``16``


Name
----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``17``


DisplayName
-----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``18``


Nickname
--------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``19``


ScreenName
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``20``


Email
-----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``21``


AdditionalEmail
---------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``22``


PhoneNumber
-----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``23``


WorkPhone
---------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``24``


HomePhone
---------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``25``


Fax
---

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``26``


Pager
-----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``27``


Mobile
------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``28``


City
----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``29``


Street
------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``30``


Title
-----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``31``


Organization
------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``32``


Department
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``33``


HasAttachmentStatus
-------------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``44``


JunkStatus
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``45``


JunkPercent
-----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``46``


JunkScoreOrigin
---------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``47``


Label
-----

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``48``


HdrProperty
-----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``49``


FolderFlag
----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``50``


Uint32HdrProperty
-----------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``51``


OtherHeader
-----------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``52``

OtherHeader MUST ALWAYS BE LAST attribute since
we can have an arbitrary # of these. The number can be changed,
however, because we never persist AttribValues as integers.

kNumMsgSearchAttributes
-----------------------

**Type**: ``nsMsgSearchAttribValue``

**Value**: ``100``


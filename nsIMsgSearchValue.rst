=================
nsIMsgSearchValue
=================

`mailnews/search/public/nsIMsgSearchValue.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchValue.idl>`_


Properties
==========

attrib
------

``attribute nsMsgSearchAttribValue attrib``

str
---

``attribute AString str``

priority
--------

``attribute nsMsgPriorityValue priority``

date
----

``attribute PRTime date``

status
------

``attribute unsigned long status``

size
----

``attribute unsigned long size``

msgKey
------

``attribute nsMsgKey msgKey``

age
---

``attribute long age``

folder
------

``attribute nsIMsgFolder folder``

label
-----

``attribute nsMsgLabelValue label``

junkStatus
----------

``attribute nsMsgJunkStatus junkStatus``

junkPercent
-----------

``attribute unsigned long junkPercent``

Methods
=======

toString
--------

``AString toString()``

Return value
^^^^^^^^^^^^

* AString

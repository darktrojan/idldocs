================
nsIMsgRuleAction
================

`mailnews/search/public/nsIMsgFilter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilter.idl>`_


Properties
==========

type
----

``attribute nsMsgRuleActionType type``

priority
--------

``attribute nsMsgPriorityValue priority``

targetFolderUri
---------------

``attribute AUTF8String targetFolderUri``

label
-----

``attribute nsMsgLabelValue label``

junkScore
---------

``attribute long junkScore``

strValue
--------

``attribute AUTF8String strValue``

customId
--------

``attribute ACString customId``

customAction
------------

``readonly attribute nsIMsgFilterCustomAction customAction``

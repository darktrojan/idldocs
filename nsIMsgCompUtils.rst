===============
nsIMsgCompUtils
===============

`mailnews/compose/public/nsIMsgCompUtils.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgCompUtils.idl>`_


Properties
==========

msgMimeConformToStandard
------------------------

``readonly attribute boolean msgMimeConformToStandard``

Methods
=======

mimeMakeSeparator
-----------------

``string mimeMakeSeparator(prefix)``

Parameters
^^^^^^^^^^

* in string prefix

Return value
^^^^^^^^^^^^

* string

msgGenerateMessageId
--------------------

``string msgGenerateMessageId(identity)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity

Return value
^^^^^^^^^^^^

* string

detectCharset
-------------

``ACString detectCharset(aContent)``

Detect the text encoding of an input string. This is a wrapper of
mozilla::EncodingDetector to be used by JavaScript code. For C++, use
MsgDetectCharsetFromFile from nsMsgUtils.cpp instead.

Parameters
^^^^^^^^^^

* in ACString aContent

Return value
^^^^^^^^^^^^

* ACString

  Detected charset.

=============
nsICMSDecoder
=============

`mailnews/extensions/smime/nsICMSDecoder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSDecoder.idl>`_

nsICMSDecoder
Streaming interface to decode an CMS message, the input data may be
passed in chunks. Cannot be called from JS.

Methods
=======

start
-----

``void start(cb, arg)``

Parameters
^^^^^^^^^^

* in NSSCMSContentCallback cb
* in voidPtr arg

update
------

``void update(aBuf, aLen)``

Parameters
^^^^^^^^^^

* in string aBuf
* in long aLen

finish
------

``void finish(msg)``

Parameters
^^^^^^^^^^

* out :doc:`nsICMSMessage` msg

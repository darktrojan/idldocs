=============
nsICMSEncoder
=============

`mailnews/extensions/smime/nsICMSEncoder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSEncoder.idl>`_

nsICMSEncoder
Interface to Encode an CMS message

Methods
=======

start
-----

``void start(aMsg, cb, arg)``

Parameters
^^^^^^^^^^

* in :doc:`nsICMSMessage` aMsg
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

``void finish()``

encode
------

``void encode(aMsg)``

Parameters
^^^^^^^^^^

* in :doc:`nsICMSMessage` aMsg

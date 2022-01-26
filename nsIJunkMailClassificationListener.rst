=================================
nsIJunkMailClassificationListener
=================================

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_


Methods
=======

onMessageClassified
-------------------

``void onMessageClassified(aMsgURI, aClassification, aJunkPercent)``

Inform a listener of a message's classification as junk. At the end
of a batch of classifications, signify end of batch by calling with
null aMsgURI (other parameters are don't care)

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in nsMsgJunkStatus aClassification
* in uint32_t aJunkPercent

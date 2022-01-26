=================================
nsIMsgTraitClassificationListener
=================================

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_


Methods
=======

onMessageTraitsClassified
-------------------------

``void onMessageTraitsClassified(aMsgURI, aTraits, aPercents)``

Inform a listener of a message's match to traits. The list
of traits being matched is in aTraits. Corresponding
indicator of match (percent) is in aPercents. At the end
of a batch of classifications, signify end of batch by calling with
null aMsgURI (other parameters are don't care)

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in Array<unsigned long> aTraits
* in Array<unsigned long> aPercents

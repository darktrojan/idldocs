=========================
nsIMsgTraitDetailListener
=========================

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_


Methods
=======

onMessageTraitDetails
---------------------

``void onMessageTraitDetails(aMsgUri, aProTrait, tokenStrings, tokenPercents, runningPercents)``

Inform a listener of details of a message's match to traits.
This returns the tokens that were used in the calculation,
the calculated percent probability that each token matches the trait,
and a running estimate (starting with the strongest tokens) of the
combined total probability that a message matches the trait, when
only tokens stronger than the current token are used.

Parameters
^^^^^^^^^^

* in AUTF8String aMsgUri
* in unsigned long aProTrait
* in Array<AString> tokenStrings
* in Array<unsigned long> tokenPercents
* in Array<unsigned long> runningPercents

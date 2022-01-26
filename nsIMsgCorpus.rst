============
nsIMsgCorpus
============

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_

The nsIMsgCorpus interface manages a corpus of mail data used for
statistical analysis of messages.

Methods
=======

clearTrait
----------

``void clearTrait(aTrait)``

Clear the corpus data for a trait id.

Parameters
^^^^^^^^^^

* in unsigned long aTrait

updateData
----------

``void updateData(aFile, aIsAdd, aFromTraits, aToTraits)``

Update corpus data from a file.
Uses the parallel arrays aFromTraits and aToTraits. These arrays allow
conversion of the trait id stored in the file (which may be originated
externally) to the trait id used in the local corpus (which is defined
locally using nsIMsgTraitService, and mapped by that interface to a
globally unique trait id string).

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in boolean aIsAdd
* in Array<unsigned long> aFromTraits
* in Array<unsigned long> aToTraits

getTokenCount
-------------

``unsigned long getTokenCount(aWord, aTrait)``

Get the corpus count for a token as a string.

Parameters
^^^^^^^^^^

* in AUTF8String aWord
* in unsigned long aTrait

Return value
^^^^^^^^^^^^

* unsigned long

  count of that token in the corpus

corpusCounts
------------

``unsigned long corpusCounts(aTrait, aMessageCount)``

Gives information on token and message count information in the
training data corpus.

Parameters
^^^^^^^^^^

* in unsigned long aTrait
* out unsigned long aMessageCount

Return value
^^^^^^^^^^^^

* unsigned long

  token count for all traits

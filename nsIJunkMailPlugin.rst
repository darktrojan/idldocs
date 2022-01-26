=================
nsIJunkMailPlugin
=================

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_


Constants
=========

UNCLASSIFIED
------------

**Type**: ``nsMsgJunkStatus``

**Value**: ``0``

Message classifications.

GOOD
----

**Type**: ``nsMsgJunkStatus``

**Value**: ``1``


JUNK
----

**Type**: ``nsMsgJunkStatus``

**Value**: ``2``


IS_SPAM_SCORE
-------------

**Type**: ``nsMsgJunkScore``

**Value**: ``100``

Message junk score constants. Junkscore can only be one of these two
values (or not set).

IS_HAM_SCORE
------------

**Type**: ``nsMsgJunkScore``

**Value**: ``0``


GOOD_TRAIT
----------

**Type**: ``unsigned long``

**Value**: ``1``

Trait ids for junk analysis. These values are fixed to ensure
backwards compatibility with existing junk-oriented classification
code.

JUNK_TRAIT
----------

**Type**: ``unsigned long``

**Value**: ``2``


Properties
==========

userHasClassified
-----------------

``readonly attribute boolean userHasClassified``

Methods
=======

classifyMessage
---------------

``void classifyMessage(aMsgURI, aMsgWindow, aListener)``

Given a message URI, determine what its current classification is
according to the current training set.

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aListener

classifyMessages
----------------

``void classifyMessages(aMsgURIs, aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in Array<AUTF8String> aMsgURIs
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aListener

classifyTraitsInMessage
-----------------------

``void classifyTraitsInMessage(aMsgURI, aProTraits, aAntiTraits, aTraitListener, aMsgWindow, aJunkListener)``

Given a message URI, evaluate its relative match to a list of
traits according to the current training set.

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in Array<unsigned long> aProTraits
* in Array<unsigned long> aAntiTraits
* in :doc:`nsIMsgTraitClassificationListener` aTraitListener
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aJunkListener

classifyTraitsInMessages
------------------------

``void classifyTraitsInMessages(aMsgURIs, aProTraits, aAntiTraits, aTraitListener, aMsgWindow, aJunkListener)``

Given an array of message URIs, evaluate their relative match to a
list of traits according to the current training set.

Parameters
^^^^^^^^^^

* in Array<AUTF8String> aMsgURIs
* in Array<unsigned long> aProTraits
* in Array<unsigned long> aAntiTraits
* in :doc:`nsIMsgTraitClassificationListener` aTraitListener
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aJunkListener

setMessageClassification
------------------------

``void setMessageClassification(aMsgURI, aOldUserClassification, aNewClassification, aMsgWindow, aListener)``

Called when a user forces the classification of a message. Should
cause the training set to be updated appropriately.
@arg aMsgURI                     URI of the message to be classified
@arg aOldUserClassification      Was it previous manually classified
by the user?  If so, how?
@arg aNewClassification          New manual classification.
@arg aListener                   Callback (may be null)

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in nsMsgJunkStatus aOldUserClassification
* in nsMsgJunkStatus aNewClassification
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aListener

setMsgTraitClassification
-------------------------

``void setMsgTraitClassification(aMsgURI, aOldTraits, aNewTraits, aTraitListener, aMsgWindow, aJunkListener)``

Called when a user forces a change in the classification of a message.
Should cause the training set to be updated appropriately.

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in Array<unsigned long> aOldTraits
* in Array<unsigned long> aNewTraits
* in :doc:`nsIMsgTraitClassificationListener` aTraitListener
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIJunkMailClassificationListener` aJunkListener

resetTrainingData
-----------------

``void resetTrainingData()``

Removes the training file and clears out any in memory training tokens.
User must retrain after doing this.
*/

detailMessage
-------------

``void detailMessage(aMsgURI, aProTrait, aAntiTrait, aListener, aMsgWindow)``

Given a message URI, return a list of tokens and their contribution to
the analysis of a message's match to a trait according to the
current training set.

Parameters
^^^^^^^^^^

* in AUTF8String aMsgURI
* in unsigned long aProTrait
* in unsigned long aAntiTrait
* in :doc:`nsIMsgTraitDetailListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

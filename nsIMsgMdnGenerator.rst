==================
nsIMsgMdnGenerator
==================

`mailnews/base/public/nsIMsgMdnGenerator.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMdnGenerator.idl>`_


Constants
=========

eDisplayed
----------

**Type**: ``EDisposeType``

**Value**: ``0``


eDispatched
-----------

**Type**: ``EDisposeType``

**Value**: ``1``


eProcessed
----------

**Type**: ``EDisposeType``

**Value**: ``2``


eDeleted
--------

**Type**: ``EDisposeType``

**Value**: ``3``


eDenied
-------

**Type**: ``EDisposeType``

**Value**: ``4``


eFailed
-------

**Type**: ``EDisposeType``

**Value**: ``5``


eDntType
--------

**Type**: ``ReceiptHdrType``

**Value**: ``0``


eRrtType
--------

**Type**: ``ReceiptHdrType``

**Value**: ``1``


eDntRrtType
-----------

**Type**: ``ReceiptHdrType``

**Value**: ``2``


eIncorporateInbox
-----------------

**Type**: ``MDNIncorporateType``

**Value**: ``0``


eIncorporateSent
----------------

**Type**: ``MDNIncorporateType``

**Value**: ``1``


Methods
=======

process
-------

``boolean process(eType, aWindow, folder, key, headers, autoAction)``

Prepare the sending of a mdn reply, and checks the prefs whether a
reply should be send. Might send the message automatically if the
prefs say it should.

Parameters
^^^^^^^^^^

* in EDisposeType eType
* in :doc:`nsIMsgWindow` aWindow
* in :doc:`nsIMsgFolder` folder
* in nsMsgKey key
* in :doc:`nsIMimeHeaders` headers
* in boolean autoAction

Return value
^^^^^^^^^^^^

* boolean

  true if the user needs to be asked for permission
  false in other cases (whether the message was sent or denied)

userAgreed
----------

``void userAgreed()``

Must be called when the user was asked for permission and agreed to
sending the mdn reply.
May only be called when |process| returned |true|. Behaviour is
unspecified in other cases

userDeclined
------------

``void userDeclined()``

Must be called when the user was asked for permission and declined to
send the mdn reply.
Will mark the message so that the user won't be asked next time.
May only be called when |process| returned |true|. Behaviour is
unspecified in other cases.

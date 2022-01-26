=============================
nsIMsgMessageFetchPartService
=============================

`mailnews/base/public/nsIMsgMessageService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMessageService.idl>`_

Some mail protocols (like imap) allow you to fetch individual mime parts. We use this interface
to represent message services whose protocols support this. To use this interface, you should get
the message service then QI for this interface. If it's present, then can fetch a mime part.

Methods
=======

fetchMimePart
-------------

``nsIURI fetchMimePart(aURI, aMessageUri, aDisplayConsumer, aMsgWindow, aUrlListener)``

Used to fetch an individual mime part

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aURI
* in AUTF8String aMessageUri
* in :doc:`nsISupports` aDisplayConsumer
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  @return

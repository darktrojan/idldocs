==============
nsINntpService
==============

`mailnews/news/public/nsINntpService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINntpService.idl>`_


Properties
==========

cacheStorage
------------

``readonly attribute nsICacheStorage cacheStorage``

Methods
=======

generateNewsHeaderValsForPosting
--------------------------------

``void generateNewsHeaderValsForPosting(newsgroupsList, newsgroupsHeaderVal, newshostHeaderVal)``

Parameters
^^^^^^^^^^

* in ACString newsgroupsList
* out string newsgroupsHeaderVal
* out string newshostHeaderVal

postMessage
-----------

``nsIURI postMessage(aFileToPost, newsgroupNames, aAccountKey, aUrlListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFileToPost
* in string newsgroupNames
* in string aAccountKey
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

getNewNews
----------

``nsIURI getNewNews(nntpServer, uri, getOld, aUrlListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsINntpIncomingServer` nntpServer
* in AUTF8String uri
* in boolean getOld
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

cancelMessage
-------------

``nsIURI cancelMessage(cancelURL, messageURI, aConsumer, aUrlListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in AUTF8String cancelURL
* in AUTF8String messageURI
* in :doc:`nsISupports` aConsumer
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

getListOfGroupsOnServer
-----------------------

``void getListOfGroupsOnServer(nntpServer, aMsgWindow, getOnlyNew)``

Parameters
^^^^^^^^^^

* in :doc:`nsINntpIncomingServer` nntpServer
* in :doc:`nsIMsgWindow` aMsgWindow
* in boolean getOnlyNew

fetchMessage
------------

``nsIURI fetchMessage(newsFolder, key, aMsgWindow, aConsumer, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` newsFolder
* in nsMsgKey key
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsISupports` aConsumer
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

downloadNewsgroupsForOffline
----------------------------

``void downloadNewsgroupsForOffline(aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener

decomposeNewsURI
----------------

``void decomposeNewsURI(uri, folder, key)``

can handle news-message:// and news://

Parameters
^^^^^^^^^^

* in AUTF8String uri
* out :doc:`nsIMsgFolder` folder
* out nsMsgKey key

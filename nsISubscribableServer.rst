=====================
nsISubscribableServer
=====================

`mailnews/base/public/nsISubscribableServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsISubscribableServer.idl>`_


Properties
==========

subscribeListener
-----------------

``attribute nsISubscribeListener subscribeListener``

delimiter
---------

``attribute char delimiter``

supportsSubscribeSearch
-----------------------

``readonly attribute boolean supportsSubscribeSearch``

folderView
----------

``readonly attribute nsITreeView folderView``

Methods
=======

startPopulating
---------------

``void startPopulating(aMsgWindow, forceToServer, getOnlyNew)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in boolean forceToServer
* in boolean getOnlyNew

startPopulatingWithUri
----------------------

``void startPopulatingWithUri(aMsgWindow, forceToServer, uri)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in boolean forceToServer
* in AUTF8String uri

stopPopulating
--------------

``void stopPopulating(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

setState
--------

``boolean setState(path, state)``

Parameters
^^^^^^^^^^

* in AUTF8String path
* in boolean state

Return value
^^^^^^^^^^^^

* boolean

subscribeCleanup
----------------

``void subscribeCleanup()``

subscribe
---------

``void subscribe(name)``

Parameters
^^^^^^^^^^

* in wstring name

unsubscribe
-----------

``void unsubscribe(name)``

Parameters
^^^^^^^^^^

* in wstring name

commitSubscribeChanges
----------------------

``void commitSubscribeChanges()``

setIncomingServer
-----------------

``void setIncomingServer(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

addTo
-----

``void addTo(aName, addAsSubscribed, aSubscribable, aChangeIfExists)``

Parameters
^^^^^^^^^^

* in AUTF8String aName
* in boolean addAsSubscribed
* in boolean aSubscribable
* in boolean aChangeIfExists

setAsSubscribed
---------------

``void setAsSubscribed(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

updateSubscribed
----------------

``void updateSubscribed()``

setShowFullName
---------------

``void setShowFullName(showFullName)``

Parameters
^^^^^^^^^^

* in boolean showFullName

hasChildren
-----------

``boolean hasChildren(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

Return value
^^^^^^^^^^^^

* boolean

isSubscribed
------------

``boolean isSubscribed(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

Return value
^^^^^^^^^^^^

* boolean

isSubscribable
--------------

``boolean isSubscribable(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

Return value
^^^^^^^^^^^^

* boolean

getLeafName
-----------

``AString getLeafName(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

Return value
^^^^^^^^^^^^

* AString

getChildURIs
------------

``Array<AUTF8String> getChildURIs(aPath)``

Returns the children uris underneath the specified uri (path).

Parameters
^^^^^^^^^^

* in AUTF8String aPath

  The server's uri; If this is null or empty, then the
  root server uri will be used.

Return value
^^^^^^^^^^^^

* Array<AUTF8String>

getFirstChildURI
----------------

``AUTF8String getFirstChildURI(path)``

Parameters
^^^^^^^^^^

* in AUTF8String path

Return value
^^^^^^^^^^^^

* AUTF8String

setSearchValue
--------------

``void setSearchValue(searchValue)``

Parameters
^^^^^^^^^^

* in AString searchValue

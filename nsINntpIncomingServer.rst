=====================
nsINntpIncomingServer
=====================

`mailnews/news/public/nsINntpIncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINntpIncomingServer.idl>`_


Properties
==========

newsrcFilePath
--------------

``attribute nsIFile newsrcFilePath``

newsrcRootPath
--------------

``attribute nsIFile newsrcRootPath``

notifyOn
--------

``attribute boolean notifyOn``

maxArticles
-----------

``attribute long maxArticles``

markOldRead
-----------

``attribute boolean markOldRead``

abbreviate
----------

``attribute boolean abbreviate``

singleSignon
------------

``attribute boolean singleSignon``

charset
-------

``attribute ACString charset``

the server charset and it may be needed to display newsgroup folder
names correctly
*/

newsrcHasChanged
----------------

``attribute boolean newsrcHasChanged``

maximumConnectionsNumber
------------------------

``attribute long maximumConnectionsNumber``

The maximum number of connections to make to the server.

This preference (internally max_cached_connections) controls how many
connections we can make. A negative connection count is treated as only
one connection, while 0 (the default) loads the default number of
connections, presently 2.

supportsExtensions
------------------

``attribute boolean supportsExtensions``

postingAllowed
--------------

``attribute boolean postingAllowed``

pushAuth
--------

``attribute boolean pushAuth``

lastUpdatedTime
---------------

``attribute unsigned long lastUpdatedTime``

firstGroupNeedingExtraInfo
--------------------------

``readonly attribute AUTF8String firstGroupNeedingExtraInfo``

Methods
=======

addNewsgroup
------------

``void addNewsgroup(name)``

Parameters
^^^^^^^^^^

* in AString name

removeNewsgroup
---------------

``void removeNewsgroup(name)``

Parameters
^^^^^^^^^^

* in AString name

writeNewsrcFile
---------------

``void writeNewsrcFile()``

displaySubscribedGroup
----------------------

``void displaySubscribedGroup(msgFolder, firstMessage, lastMessage, totalMessages)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgNewsFolder` msgFolder
* in long firstMessage
* in long lastMessage
* in long totalMessages

getNntpChannel
--------------

``nsIChannel getNntpChannel(uri, window)``

Get a new NNTP channel to run the URI.

If the server has used up all of its connections, this will place the URI
in the queue to be run when one is freed.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` uri
* in :doc:`nsIMsgWindow` window

Return value
^^^^^^^^^^^^

* :doc:`nsIChannel`

loadNewsUrl
-----------

``void loadNewsUrl(uri, window, consumer)``

Enqueues a URI to be run when we have a free connection.

If there is one already free, it will be immediately started.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` uri
* in :doc:`nsIMsgWindow` window
* in :doc:`nsISupports` consumer

removeConnection
----------------

``void removeConnection(aNntpConnection)``

Remove a connection from our connection cache.

Parameters
^^^^^^^^^^

* in :doc:`nsINNTPProtocol` aNntpConnection

prepareForNextUrl
-----------------

``void prepareForNextUrl(aNntpConnection)``

Load the next URI in the queue to the given connection.

Parameters
^^^^^^^^^^

* in nsNNTPProtocol aNntpConnection

containsNewsgroup
-----------------

``boolean containsNewsgroup(escapedName)``

Returns whether or not the server has subscribed to the given newsgroup.

Note that the name here is intended to be escaped; however, since `%' is
not a legal newsgroup name, it is possibly safe to pass in an unescaped
newsgroup name.

Parameters
^^^^^^^^^^

* in AUTF8String escapedName

Return value
^^^^^^^^^^^^

* boolean

subscribeToNewsgroup
--------------------

``void subscribeToNewsgroup(name)``

Parameters
^^^^^^^^^^

* in AUTF8String name

addNewsgroupToList
------------------

``void addNewsgroupToList(name)``

Parameters
^^^^^^^^^^

* in string name

addExtension
------------

``void addExtension(extension)``

Parameters
^^^^^^^^^^

* in string extension

queryExtension
--------------

``boolean queryExtension(extension)``

Parameters
^^^^^^^^^^

* in string extension

Return value
^^^^^^^^^^^^

* boolean

addPropertyForGet
-----------------

``void addPropertyForGet(name, value)``

Parameters
^^^^^^^^^^

* in string name
* in string value

queryPropertyForGet
-------------------

``string queryPropertyForGet(name)``

Parameters
^^^^^^^^^^

* in string name

Return value
^^^^^^^^^^^^

* string

addSearchableGroup
------------------

``void addSearchableGroup(name)``

Parameters
^^^^^^^^^^

* in AString name

querySearchableGroup
--------------------

``boolean querySearchableGroup(name)``

Parameters
^^^^^^^^^^

* in AString name

Return value
^^^^^^^^^^^^

* boolean

addSearchableHeader
-------------------

``void addSearchableHeader(headerName)``

Parameters
^^^^^^^^^^

* in string headerName

querySearchableHeader
---------------------

``boolean querySearchableHeader(headerName)``

Parameters
^^^^^^^^^^

* in string headerName

Return value
^^^^^^^^^^^^

* boolean

findGroup
---------

``nsIMsgNewsFolder findGroup(name)``

Returns the folder corresponding to the given group.

Note that this name is expected to be unescaped.
@note If the group does not exist, a bogus news folder will be returned.
DO NOT call this method unless you are sure that the newsgroup
is subscribed to (e.g., by containsNewsgroup)

Parameters
^^^^^^^^^^

* in AUTF8String name

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgNewsFolder`

setGroupNeedsExtraInfo
----------------------

``void setGroupNeedsExtraInfo(name, needsExtraInfo)``

Parameters
^^^^^^^^^^

* in AUTF8String name
* in boolean needsExtraInfo

groupNotFound
-------------

``void groupNotFound(window, group, opening)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` window
* in AString group
* in boolean opening

setPrettyNameForGroup
---------------------

``void setPrettyNameForGroup(name, prettyName)``

Parameters
^^^^^^^^^^

* in AString name
* in AString prettyName

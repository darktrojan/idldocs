=================
nsIMsgFolderCache
=================

`mailnews/base/public/nsIMsgFolderCache.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolderCache.idl>`_

nsIMsgFolderCache is a store of values which might be slow for the folder
to calculate. For example: the number of unread messages.
The account manager holds the cache, and each folder manipulates its cached
properties via nsIMsgFolderCacheElement.

Methods
=======

init
----

``void init(cacheFile, legacyFile)``

Set up the cache, loading/saving to cacheFile.
If a new-style cacheFile isn't found, it looks for an old panacea.dat,
specified by legacyFile and migrates it to the new format.
Neither file has to exist - it'll just start up with an empty cache.
nsMsgFolderCache (the only implementation) will autosave to cacheFile
when changes are made.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` cacheFile
* in :doc:`nsIFile` legacyFile

getCacheElement
---------------

``nsIMsgFolderCacheElement getCacheElement(key, createIfMissing)``

Return an nsIMsgFolderCacheElement for a given folder.
Unless createIfMissing is set, a missing entry will cause failure.

Parameters
^^^^^^^^^^

* in ACString key
* in boolean createIfMissing

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolderCacheElement`

removeElement
-------------

``void removeElement(key)``

Parameters
^^^^^^^^^^

* in ACString key

flush
-----

``void flush()``

Write immediately to cacheFile if any data has been changed.
This happens in the cache dtor anyway, and is exposed here purely for
unit testing (so tests don't have to wait for JS garbage collection).

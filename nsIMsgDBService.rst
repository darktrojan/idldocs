===============
nsIMsgDBService
===============

`mailnews/db/msgdb/public/nsIMsgDatabase.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIMsgDatabase.idl>`_

A service to open mail databases and manipulate listeners automatically.

The contract ID for this component is
<tt>\@mozilla.org/msgDatabase/msgDBService;1</tt>.

Properties
==========

openDBs
-------

``readonly attribute Array<nsIMsgDatabase> openDBs``

Methods
=======

openFolderDB
------------

``nsIMsgDatabase openFolderDB(aFolder, aLeaveInvalidDB)``

Opens a database for a given folder.
This method is preferred over nsIMsgDBService::openMailDBFromFile if the
caller has an actual nsIMsgFolder around. If the database detects that it
is unreadable or out of date (using nsIMsgDatabase::outOfDate) it will
destroy itself and prepare to be rebuilt, unless aLeaveInvalidDB is true.
If one gets a NS_MSG_ERROR_FOLDER_SUMMARY_MISSING message, then one
should call nsIMsgDBService::createNewDB to create the new database.
@see nsIMsgDatabase::Open
@see nsIMsgDBService::createNewDB

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in boolean aLeaveInvalidDB

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

  A new nsIMsgDatabase object representing the folder
  database that was opened.

Throws
^^^^^^

* NS_ERROR_FILE_TARGET_DOES_NOT_EXIST
  The file could not be created.
* NS_MSG_ERROR_FOLDER_SUMMARY_OUT_OF_DATE
  The database is present (and was opened), but the
  summary file is out of date.
* NS_MSG_ERROR_FOLDER_SUMMARY_MISSING
  The database is present, but the summary file is
  missing.

asyncOpenFolderDB
-----------------

``nsIMsgDatabase asyncOpenFolderDB(aFolder, aLeaveInvalidDB)``

This is the same as a synchronous open in terms of params and errors.
But to finish opening the db, the caller must call
nsIMsgDBService::OpenMore repeatedly until the open is finished.
@see nsIMsgDBService::openFolderDB
@see nsIMsgDBService::openMore

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in boolean aLeaveInvalidDB

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

openMore
--------

``boolean openMore(aDB, aTimeHint)``

Continues the open process for a db opened with
nsIMsgDBService::asyncOpenFolderDB. Returns true if the db is ready
to use, false if openMore needs to be called again.
This will throw the same kinds of exceptions as openFolderDB.
@see nsIMsgDBService::openFolderDB

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDatabase` aDB
* in unsigned long aTimeHint

Return value
^^^^^^^^^^^^

* boolean

  true if db is ready to use, false if openMore needs to
  be called again.

createNewDB
-----------

``nsIMsgDatabase createNewDB(aFolder)``

Creates a new database for the given folder.
If the database already exists, it will return the database, emit a
warning, but not fully initialize it. For this reason, it should only be
used when it is known that the database does not exist, such as when
nsIMsgDBService::openFolderDB throws an error.
@see nsIMsgDBService::openFolderDB

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

openMailDBFromFile
------------------

``nsIMsgDatabase openMailDBFromFile(aFile, aFolder, aCreate, aLeaveInvalidDB)``

Opens or creates a database for a given file.
This method should only be used if the caller does not have a folder
instance, because the resulting db and message headers retrieved from the
database would not know their owning folder, which limits their usefulness.
For this reason, one should use nsIMsgDBService::openFolderDB instead
except under special circumstances.
Unlike nsIMsgDBService::openFolderDB, there is no corresponding method to
create a new database if opening the database failed. However, this method
will never throw NS_MSG_ERROR_FOLDER_SUMMARY_MISSING, so no corresponding
method is needed.
@see nsIMsgDBService::openFolderDB
@see nsIMsgDatabase::Open

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in :doc:`nsIMsgFolder` aFolder
* in boolean aCreate
* in boolean aLeaveInvalidDB

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

  A new nsIMsgDatabase object encapsulating the file
  passed in.

Throws
^^^^^^

* NS_ERROR_FILE_TARGET_DOES_NOT_EXIST
  The file could not be created.

registerPendingListener
-----------------------

``void registerPendingListener(aFolder, aListener)``

Adds the given listener to the listener set for the folder.
Since the message database will likely be opened and closed many times, by
registering using this method, one will be guaranteed to see all subsequent
modifications. This will also add the listener to the database if it is
already opened.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIDBChangeListener` aListener

unregisterPendingListener
-------------------------

``void unregisterPendingListener(aListener)``

Removes the listener from all folder listener sets.

Parameters
^^^^^^^^^^

* in :doc:`nsIDBChangeListener` aListener

Throws
^^^^^^

* NS_ERROR_FAILURE
  The listener is not registered.

cachedDBForFolder
-----------------

``nsIMsgDatabase cachedDBForFolder(aFolder)``

Get the db for a folder, if already open.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

  null if the db isn't open, otherwise the db.

forceFolderDBClosed
-------------------

``void forceFolderDBClosed(aFolder)``

Close the db for a folder, if already open.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

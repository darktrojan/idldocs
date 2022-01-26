====================
nsIMsgAccountManager
====================

`mailnews/base/public/nsIMsgAccountManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgAccountManager.idl>`_


Properties
==========

defaultAccount
--------------

``attribute nsIMsgAccount defaultAccount``

Returns the account that was marked as the default one.
Only some server types can serve as default account.
If there is no such account, null is returned.
You can only set the defaultAccount to an
account already in the account manager.

accounts
--------

``readonly attribute Array<nsIMsgAccount> accounts``

Ordered list of all accounts, by the order they are in the prefs.
Accounts with hidden servers are not returned.
array of nsIMsgAccount

allIdentities
-------------

``readonly attribute Array<nsIMsgIdentity> allIdentities``

allServers
----------

``readonly attribute Array<nsIMsgIncomingServer> allServers``

folderCache
-----------

``readonly attribute nsIMsgFolderCache folderCache``

shutdownInProgress
------------------

``readonly attribute boolean shutdownInProgress``

userNeedsToAuthenticate
-----------------------

``attribute boolean userNeedsToAuthenticate``

for preventing unauthenticated users from seeing header information

localFoldersServer
------------------

``attribute nsIMsgIncomingServer localFoldersServer``

allFolders
----------

``readonly attribute Array<nsIMsgFolder> allFolders``

Methods
=======

getUniqueAccountKey
-------------------

``ACString getUniqueAccountKey()``

Return value
^^^^^^^^^^^^

* ACString

createAccount
-------------

``nsIMsgAccount createAccount()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgAccount`

getAccount
----------

``nsIMsgAccount getAccount(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgAccount`

removeAccount
-------------

``void removeAccount(aAccount, aRemoveFiles)``

Removes the account from the list of accounts.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgAccount` aAccount
* in boolean aRemoveFiles

createIdentity
--------------

``nsIMsgIdentity createIdentity()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIdentity`

getUniqueServerKey
------------------

``ACString getUniqueServerKey()``

Scan the preferences to find a unique server key.

Return value
^^^^^^^^^^^^

* ACString

createIncomingServer
--------------------

``nsIMsgIncomingServer createIncomingServer(username, hostname, type)``

Parameters
^^^^^^^^^^

* in ACString username
* in ACString hostname
* in ACString type

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIncomingServer`

removeIncomingServer
--------------------

``void removeIncomingServer(aServer, aRemoveFiles)``

Removes the server from the list of servers
@throws NS_ERROR_FAILURE if server not found

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` aServer
* in boolean aRemoveFiles

getIdentity
-----------

``nsIMsgIdentity getIdentity(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIdentity`

getIncomingServer
-----------------

``nsIMsgIncomingServer getIncomingServer(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIncomingServer`

FindServer
----------

``nsIMsgIncomingServer FindServer(userName, hostname, type)``

Parameters
^^^^^^^^^^

* in ACString userName
* in ACString hostname
* in ACString type

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIncomingServer`

findServerByURI
---------------

``nsIMsgIncomingServer findServerByURI(aURI, aRealFlag)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aURI
* in boolean aRealFlag

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIncomingServer`

findRealServer
--------------

``nsIMsgIncomingServer findRealServer(userName, hostname, type, port)``

Parameters
^^^^^^^^^^

* in ACString userName
* in ACString hostname
* in ACString type
* in long port

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIncomingServer`

FindServerIndex
---------------

``long FindServerIndex(server)``

find the index of this server in the (ordered) list of accounts

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* long

FindAccountForServer
--------------------

``nsIMsgAccount FindAccountForServer(server)``

Finds an account for the given incoming server.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgAccount`

  If found, the nsIMsgAccount representing the account found.
  Otherwise returns null.

getIdentitiesForServer
----------------------

``Array<nsIMsgIdentity> getIdentitiesForServer(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgIdentity`>

getFirstIdentityForServer
-------------------------

``nsIMsgIdentity getFirstIdentityForServer(server)``

given a server, return the first identity in accounts that have this server

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgIdentity`

getServersForIdentity
---------------------

``Array<nsIMsgIncomingServer> getServersForIdentity(identity)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgIncomingServer`>

createLocalMailAccount
----------------------

``void createLocalMailAccount()``

LoadAccounts
------------

``void LoadAccounts()``

ReactivateAccounts
------------------

``void ReactivateAccounts()``

When the server for an account could not be loaded, typically because the
extension providing it could not be loaded, it is deactivated for a period
of time as documented in nsIMsgAccount.idl. The server is normally only
rechecked at startup but this function can be used to recheck all servers
at any time to avoid having to restart to reactivate an account.

setSpecialFolders
-----------------

``void setSpecialFolders()``

loadVirtualFolders
------------------

``void loadVirtualFolders()``

UnloadAccounts
--------------

``void UnloadAccounts()``

WriteToFolderCache
------------------

``void WriteToFolderCache(folderCache)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolderCache` folderCache

saveVirtualFolders
------------------

``void saveVirtualFolders()``

closeCachedConnections
----------------------

``void closeCachedConnections()``

shutdownServers
---------------

``void shutdownServers()``

CleanupOnExit
-------------

``void CleanupOnExit()``

SetFolderDoingEmptyTrash
------------------------

``void SetFolderDoingEmptyTrash(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

GetEmptyTrashInProgress
-----------------------

``boolean GetEmptyTrashInProgress()``

Return value
^^^^^^^^^^^^

* boolean

SetFolderDoingCleanupInbox
--------------------------

``void SetFolderDoingCleanupInbox(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

GetCleanupInboxInProgress
-------------------------

``boolean GetCleanupInboxInProgress()``

Return value
^^^^^^^^^^^^

* boolean

addRootFolderListener
---------------------

``void addRootFolderListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` listener

removeRootFolderListener
------------------------

``void removeRootFolderListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` listener

addIncomingServerListener
-------------------------

``void addIncomingServerListener(serverListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIIncomingServerListener` serverListener

removeIncomingServerListener
----------------------------

``void removeIncomingServerListener(serverListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIIncomingServerListener` serverListener

notifyServerLoaded
------------------

``void notifyServerLoaded(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

notifyServerUnloaded
--------------------

``void notifyServerUnloaded(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

notifyServerChanged
-------------------

``void notifyServerChanged(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

saveAccountInfo
---------------

``void saveAccountInfo()``

getChromePackageName
--------------------

``ACString getChromePackageName(aExtensionName)``

Parameters
^^^^^^^^^^

* in ACString aExtensionName

Return value
^^^^^^^^^^^^

* ACString

folderUriForPath
----------------

``AUTF8String folderUriForPath(aLocalPath)``

Iterates over all folders looking for one with the passed in path,
and returns the uri for the matching folder. In the future,
the folder lookup service will provide this functionality.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aLocalPath

Return value
^^^^^^^^^^^^

* AUTF8String

  the URI of the folder that corresponds to aLocalPath

getSortOrder
------------

``long getSortOrder(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* long

reorderAccounts
---------------

``void reorderAccounts(accountKeys)``

Sets new order of accounts.

Parameters
^^^^^^^^^^

* in Array<ACString> accountKeys

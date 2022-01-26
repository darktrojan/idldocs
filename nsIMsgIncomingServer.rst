====================
nsIMsgIncomingServer
====================

`mailnews/base/public/nsIMsgIncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgIncomingServer.idl>`_


Constants
=========

keepDups
--------

**Type**: ``long``

**Value**: ``0``


deleteDups
----------

**Type**: ``long``

**Value**: ``1``


moveDupsToTrash
---------------

**Type**: ``long``

**Value**: ``2``


markDupsRead
------------

**Type**: ``long``

**Value**: ``3``


Properties
==========

key
---

``attribute ACString key``

internal pref key - guaranteed to be unique across all servers

prettyName
----------

``attribute AString prettyName``

pretty name - should be "userid on hostname"
if the pref is not set

constructedPrettyName
---------------------

``readonly attribute AString constructedPrettyName``

helper function to construct the pretty name in a server type
specific way - e.g., mail for foo@test.com, news on news.mozilla.org

hostName
--------

``attribute AUTF8String hostName``

hostname of the server

realHostName
------------

``attribute AUTF8String realHostName``

real hostname of the server (if server name is changed it's stored here)

port
----

``attribute long port``

username
--------

``attribute AUTF8String username``

userid to log into the server

realUsername
------------

``attribute AUTF8String realUsername``

real username of the server (if username is changed it's stored here)

type
----

``attribute ACString type``

protocol type, i.e. "pop3", "imap", "nntp", "none", etc
used to construct URLs

clientid
--------

``attribute ACString clientid``

The CLIENTID to use for this server.
@see https://tools.ietf.org/html/draft-yu-imap-client-id-01

clientidEnabled
---------------

``attribute boolean clientidEnabled``

Whether the CLIENTID feature above is enabled.

protocolInfo
------------

``readonly attribute nsIMsgProtocolInfo protocolInfo``

The proper instance of nsIMsgProtocolInfo corresponding to this server type.

accountManagerChrome
--------------------

``readonly attribute AString accountManagerChrome``

localStoreType
--------------

``readonly attribute ACString localStoreType``

The schema for the local mail store, such as "mailbox", "imap", or "news"
used to construct URIs. The contractID for the nsIMsgMessageService
implementation that will manage access to messages associated with this
server is constructed using this type.

localDatabaseType
-----------------

``readonly attribute ACString localDatabaseType``

The schema for the nsIMsgDatabase implementation, such as "mailbox" or
"imap", that will be used to construct the database instance used by
message folders associated with this server.

password
--------

``attribute AString password``

downloadOnBiff
--------------

``attribute boolean downloadOnBiff``

doBiff
------

``attribute boolean doBiff``

biffMinutes
-----------

``attribute long biffMinutes``

biffState
---------

``attribute unsigned long biffState``

performingBiff
--------------

``attribute boolean performingBiff``

localPath
---------

``attribute nsIFile localPath``

msgStore
--------

``readonly attribute nsIMsgPluggableStore msgStore``

serverURI
---------

``readonly attribute AUTF8String serverURI``

rootFolder
----------

``attribute nsIMsgFolder rootFolder``

rootMsgFolder
-------------

``readonly attribute nsIMsgFolder rootMsgFolder``

serverBusy
----------

``attribute boolean serverBusy``

isSecure
--------

``readonly attribute boolean isSecure``

Is the server using a secure channel (SSL or STARTTLS).

authMethod
----------

``attribute nsMsgAuthMethodValue authMethod``

Authentication mechanism.

@see nsMsgAuthMethod (in MailNewsTypes2.idl)
Same as "mail.server...authMethod" pref

socketType
----------

``attribute nsMsgSocketTypeValue socketType``

Whether to SSL or STARTTLS or not

@see nsMsgSocketType (in MailNewsTypes2.idl)
Same as "mail.server...socketType" pref

emptyTrashOnExit
----------------

``attribute boolean emptyTrashOnExit``

serverRequiresPasswordForBiff
-----------------------------

``readonly attribute boolean serverRequiresPasswordForBiff``

valid
-----

``attribute boolean valid``

downloadMessagesAtStartup
-------------------------

``readonly attribute boolean downloadMessagesAtStartup``

canHaveFilters
--------------

``attribute boolean canHaveFilters``

canDelete
---------

``attribute boolean canDelete``

can this server be removed from the account manager?  for
instance, local mail is not removable, but an imported folder is

loginAtStartUp
--------------

``attribute boolean loginAtStartUp``

limitOfflineMessageSize
-----------------------

``attribute boolean limitOfflineMessageSize``

maxMessageSize
--------------

``attribute long maxMessageSize``

retentionSettings
-----------------

``attribute nsIMsgRetentionSettings retentionSettings``

canBeDefaultServer
------------------

``readonly attribute boolean canBeDefaultServer``

canSearchMessages
-----------------

``readonly attribute boolean canSearchMessages``

canEmptyTrashOnExit
-------------------

``readonly attribute boolean canEmptyTrashOnExit``

displayStartupPage
------------------

``attribute boolean displayStartupPage``

downloadSettings
----------------

``attribute nsIMsgDownloadSettings downloadSettings``

offlineSupportLevel
-------------------

``attribute long offlineSupportLevel``

supportsDiskSpace
-----------------

``readonly attribute boolean supportsDiskSpace``

hidden
------

``attribute boolean hidden``

Hide this server/account from the UI - used for smart mailboxes.
The server can be retrieved from the account manager by name using the
various Find methods, but nsIMsgAccountManager's GetAccounts and
GetAllServers methods won't return the server/account.

defaultCopiesAndFoldersPrefsToServer
------------------------------------

``attribute boolean defaultCopiesAndFoldersPrefsToServer``

If the server supports Fcc/Sent/etc, default prefs can point to
the server. Otherwise, copies and folders prefs should point to
Local Folders.

By default this value is set to true via global pref 'allows_specialfolders_usage'
(mailnews.js). For Nntp, the value is overridden to be false.
If ISPs want to modify this value, they should do that in their rdf file
by using this attribute. Please look at mozilla/mailnews/base/ispdata/aol.rdf for
usage example.

canCreateFoldersOnServer
------------------------

``attribute boolean canCreateFoldersOnServer``

canFileMessagesOnServer
-----------------------

``attribute boolean canFileMessagesOnServer``

canCompactFoldersOnServer
-------------------------

``readonly attribute boolean canCompactFoldersOnServer``

canUndoDeleteOnServer
---------------------

``readonly attribute boolean canUndoDeleteOnServer``

filterScope
-----------

``readonly attribute nsMsgSearchScopeValue filterScope``

searchScope
-----------

``readonly attribute nsMsgSearchScopeValue searchScope``

passwordPromptRequired
----------------------

``readonly attribute boolean passwordPromptRequired``

If the password for the server is available either via authentication
in the current session or from password manager stored entries, return
false. Otherwise, return true. If password is obtained from password
manager, set the password member variable.

spamSettings
------------

``readonly attribute nsISpamSettings spamSettings``

spam settings

spamFilterPlugin
----------------

``readonly attribute nsIMsgFilterPlugin spamFilterPlugin``

isDeferredTo
------------

``readonly attribute boolean isDeferredTo``

incomingDuplicateAction
-----------------------

``attribute long incomingDuplicateAction``

sortOrder
---------

``readonly attribute long sortOrder``

Return the order in which this server type should appear in the folder pane.
This sort order is a number between 100000000 and 900000000 so that RDF can
use it as a string.
The current return values are these:
0 = default account,       100000000 = mail accounts (POP3/IMAP4),
200000000 = Local Folders, 300000000 = IM accounts,
400000000 = RSS,           500000000 = News
If a new server type is created a TB UI reviewer must decide its sort order.

Methods
=======

onUserOrHostNameChanged
-----------------------

``void onUserOrHostNameChanged(oldName, newName, hostnameChanged)``

Parameters
^^^^^^^^^^

* in AUTF8String oldName
* in AUTF8String newName
* in bool hostnameChanged

getPasswordWithUI
-----------------

``AString getPasswordWithUI(aPromptString, aPromptTitle, aMsgWindow)``

Attempts to get the password first from the password manager, if that
fails it will attempt to get it from the user if aMsgWindow is supplied.
@note NS_MSG_PASSWORD_PROMPT_CANCELLED is a success code that is returned
if the prompt was presented to the user but the user cancelled the
prompt.

Parameters
^^^^^^^^^^

* in AString aPromptString
* in AString aPromptTitle
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* AString

  The obtained password. Could be an empty password.

Throws
^^^^^^

* NS_ERROR_FAILURE  The password could not be obtained.

forgetPassword
--------------

``void forgetPassword()``

forgetSessionPassword
---------------------

``void forgetSessionPassword()``

getFilterList
-------------

``nsIMsgFilterList getFilterList(aMsgWindow)``

Get the server's list of filters.
This SHOULD be the same filter list as the root folder's, if the server
supports per-folder filters. Furthermore, this list SHOULD be used for all
incoming messages.
Since the returned nsIMsgFilterList is mutable, it is not necessary to call
setFilterList after the filters have been changed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

  The list of filters.

setFilterList
-------------

``void setFilterList(aFilterList)``

Set the server's list of filters.
Note that this does not persist the filter list. To change the contents
of the existing filters, use getFilterList and mutate the values as
appropriate.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` aFilterList

getEditableFilterList
---------------------

``nsIMsgFilterList getEditableFilterList(aMsgWindow)``

Get user editable filter list. This does not have to be the same as
the filterlist above, typically depending on the users preferences.
The filters in this list are not processed, but only to be edited by
the user.
@see getFilterList

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

  The list of filters.

setEditableFilterList
---------------------

``void setEditableFilterList(aFilterList)``

Set user editable filter list.
This does not persist the filterlist, @see setFilterList
@see getEditableFilterList
@see setFilterList

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` aFilterList

setDefaultLocalPath
-------------------

``void setDefaultLocalPath(aDefaultLocalPath)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aDefaultLocalPath

verifyLogon
-----------

``nsIURI verifyLogon(aUrlListener, aMsgWindow)``

Verify that we can logon

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aUrlListener

  gets called back with success or failure.
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  - the url that we run.

performBiff
-----------

``void performBiff(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

getNewMessages
--------------

``void getNewMessages(aFolder, aMsgWindow, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener

performExpand
-------------

``void performExpand(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

writeToFolderCache
------------------

``void writeToFolderCache(folderCache)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolderCache` folderCache

closeCachedConnections
----------------------

``void closeCachedConnections()``

shutdown
--------

``void shutdown()``

getBoolValue
------------

``boolean getBoolValue(attr)``

Get or set the value as determined by the preference tree.
These methods MUST NOT fail if the preference is not set, and therefore
they MUST have a default value. This default value is provided in practice
by use of a default preference tree. The standard format for the pref
branches are <tt>mail.server.<i>key</i>.</tt> for per-server preferences,
such that the preference is <tt>mail.server.<i>key</i>.<i>attr</i></tt>.
The attributes are passed in as strings for ease of access by the C++
consumers of this method.
@{

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* boolean

  The value of the preference.

setBoolValue
------------

``void setBoolValue(attr, value)``

Parameters
^^^^^^^^^^

* in string attr
* in boolean value

getCharValue
------------

``ACString getCharValue(attr)``

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* ACString

setCharValue
------------

``void setCharValue(attr, value)``

Parameters
^^^^^^^^^^

* in string attr
* in ACString value

getUnicharValue
---------------

``AString getUnicharValue(attr)``

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* AString

setUnicharValue
---------------

``void setUnicharValue(attr, value)``

Parameters
^^^^^^^^^^

* in string attr
* in AString value

getIntValue
-----------

``long getIntValue(attr)``

Parameters
^^^^^^^^^^

* in string attr

Return value
^^^^^^^^^^^^

* long

setIntValue
-----------

``void setIntValue(attr, value)``

Parameters
^^^^^^^^^^

* in string attr
* in long value

getFileValue
------------

``nsIFile getFileValue(relpref, abspref)``

@} */
Get or set the value as determined by the preference tree.
These methods MUST NOT fail if the preference is not set, and therefore
they MUST have a default value. This default value is provided in practice
by use of a default preference tree. The standard format for the pref
branches are <tt>mail.server.<i>key</i>.</tt> for per-server preferences,
such that the preference is <tt>mail.server.<i>key</i>.<i>attr</i></tt>.
The attributes are passed in as strings for ease of access by the C++
consumers of this method.
There are two preference names on here for legacy reasons, where the first
is the name which will be using a (preferred) relative preference and the
second a deprecated absolute preference. Implementations that do not have
to worry about supporting legacy preferences can safely ignore this second
parameter. Callers must still provide a valid value, though.
@{

Parameters
^^^^^^^^^^

* in string relpref
* in string abspref

Return value
^^^^^^^^^^^^

* :doc:`nsIFile`

  The value of the preference.

setFileValue
------------

``void setFileValue(relpref, abspref, aValue)``

Parameters
^^^^^^^^^^

* in string relpref
* in string abspref
* in :doc:`nsIFile` aValue

clearAllValues
--------------

``void clearAllValues()``

@} */
this is really dangerous. this destroys all pref values
do not call this unless you know what you're doing!

removeFiles
-----------

``void removeFiles()``

This is also very dangerous. This will low-level remove the files
associated with this server on disk. It does not notify any listeners.

toString
--------

``AString toString()``

Return value
^^^^^^^^^^^^

* AString

displayOfflineMsg
-----------------

``void displayOfflineMsg(aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow

equals
------

``boolean equals(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

Return value
^^^^^^^^^^^^

* boolean

generatePrettyNameForMigration
------------------------------

``AString generatePrettyNameForMigration()``

Return value
^^^^^^^^^^^^

* AString

configureTemporaryFilters
-------------------------

``void configureTemporaryFilters(filterList)``

for mail, this configures both the MDN filter, and the server-side
spam filter filters, if needed.
If we have set up to filter return receipts into
our Sent folder, this utility method creates
a filter to do that, and adds it to our filterList
if it doesn't exist.  If it does, it will enable it.
this is not used by news filters (yet).

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` filterList

clearTemporaryReturnReceiptsFilter
----------------------------------

``void clearTemporaryReturnReceiptsFilter()``

If Sent folder pref is changed we need to clear the temporary
return receipt filter so that the new return receipt filter can
be recreated (by ConfigureTemporaryReturnReceiptsFilter()).

getMsgFolderFromURI
-------------------

``nsIMsgFolder getMsgFolderFromURI(aFolderResource, aURI)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolderResource
* in AUTF8String aURI

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

isNewHdrDuplicate
-----------------

``boolean isNewHdrDuplicate(aNewHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aNewHdr

Return value
^^^^^^^^^^^^

* boolean

setForcePropertyEmpty
---------------------

``void setForcePropertyEmpty(propertyName, aForcePropertyEmpty)``

Set a boolean to force an inherited propertyName to return empty instead
of inheriting from a parent folder, server, or the global

Parameters
^^^^^^^^^^

* in string propertyName
* in boolean aForcePropertyEmpty

getForcePropertyEmpty
---------------------

``boolean getForcePropertyEmpty(propertyName)``

Get a boolean to force an inherited propertyName to return empty instead
of inheriting from a parent folder, server, or the global

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* boolean

  true if an empty inherited property should be returned

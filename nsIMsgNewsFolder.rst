================
nsIMsgNewsFolder
================

`mailnews/news/public/nsIMsgNewsFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsIMsgNewsFolder.idl>`_


Properties
==========

unicodeName
-----------

``readonly attribute AString unicodeName``

rawName
-------

``readonly attribute ACString rawName``

|rawName| is an 8-bit string to represent the name of a newsgroup used by
a news server. It's offered for the convenience of callers so that they
don't have to convert |unicodeName| to the server-side name when
communicating with a news server.  It's US-ASCII except for some
'stand-alone' Chinese news servers that use GB2312 for newsgroup names
violating RFC 1036. For those servers, it's GB2312. However, it can be any
other single and multibyte encoding in principle. The encoding of this
string is stored in |nsINntpIncomingServer| because that's a server-wide
property.
*/

nntpServer
----------

``readonly attribute nsINntpIncomingServer nntpServer``

saveArticleOffline
------------------

``attribute boolean saveArticleOffline``

groupUsername
-------------

``attribute ACString groupUsername``

groupPassword
-------------

``attribute ACString groupPassword``

charset
-------

``readonly attribute ACString charset``

newsrcLine
----------

``readonly attribute AUTF8String newsrcLine``

optionLines
-----------

``readonly attribute ACString optionLines``

unsubscribedNewsgroupLines
--------------------------

``readonly attribute ACString unsubscribedNewsgroupLines``

Methods
=======

getAuthenticationCredentials
----------------------------

``bool getAuthenticationCredentials(aMsgWindow, mayPrompt, mustPrompt)``

@name Authentication methods
NNTP authentication is slightly wonky, due to edge cases that are not seen
in other protocols. Authentication is not necessary; if authentication is
used, it could be configured on a per-group basis or even require only a
username and not a password.

Since passwords could be per-group, it is necessary to refer to passwords
using the methods on this interface and not nsIMsgIncomingServer. Passwords
for the server as a whole are found via the root folder. If the server is
configured to use single sign-on (the default), asking any group for its
password will result in the server's password, otherwise, each group stores
its password individually.

Due to this setup, most of the password management functions on
nsIMsgIncomingServer do not correctly work. The only one that would affect
the passwords stored on folders correctly is forgetPassword; using any
other on a news server would result in inconsistent state.

Before requesting either the username or password for authentication, it is
first necessary to call getAuthenticationCredentials. If the method returns
true, then groupUsername and groupPassword are appropriately set up for
necessary authentication; if not, then authentication must be stopped.
Gets the authentication credentials, returning if the results are valid.

If mustPrompt is true, then the user will always be asked for the
credentials. Otherwise, if mayPrompt is true, then the user will be asked
for credentials if there are no saved credentials. If mayPrompt is false,
then no prompt will be shown, even if there are no saved credentials.

If this method returns true, then groupUsername and groupPassword will
contain non-empty results that could be used for authentication. If this
method returns false, then the values of groupUsername and groupPassword
will be cleared if they had previously been set. This could happen if
mustPrompt were true and the user decided to cancel the authentication
prompt.

Note that this method will be executed synchronously; if an async prompt
is wanted, it is the responsibility of the caller to manage it explicitly
with nsIMsgAsyncPrompter.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in bool mayPrompt
* in bool mustPrompt

Return value
^^^^^^^^^^^^

* bool

forgetAuthenticationCredentials
-------------------------------

``void forgetAuthenticationCredentials()``

moveFolder
----------

``void moveFolder(aNewsgroupToMove, aRefNewsgroup, aOrientation)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aNewsgroupToMove
* in :doc:`nsIMsgFolder` aRefNewsgroup
* in int32_t aOrientation

addNewsgroup
------------

``nsIMsgFolder addNewsgroup(newsgroupName, setStr)``

Parameters
^^^^^^^^^^

* in AUTF8String newsgroupName
* in ACString setStr

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

setReadSetFromStr
-----------------

``void setReadSetFromStr(setStr)``

Parameters
^^^^^^^^^^

* in ACString setStr

SetNewsrcHasChanged
-------------------

``void SetNewsrcHasChanged(newsrcHasChanged)``

Parameters
^^^^^^^^^^

* in boolean newsrcHasChanged

updateSummaryFromNNTPInfo
-------------------------

``void updateSummaryFromNNTPInfo(oldest, youngest, total)``

Parameters
^^^^^^^^^^

* in long oldest
* in long youngest
* in long total

removeMessage
-------------

``void removeMessage(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

removeMessages
--------------

``void removeMessages(aMsgKeys)``

Parameters
^^^^^^^^^^

* in nsMsgKeyArrayRef aMsgKeys

cancelComplete
--------------

``void cancelComplete()``

cancelFailed
------------

``void cancelFailed()``

getMessageIdForKey
------------------

``ACString getMessageIdForKey(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* ACString

getNextNMessages
----------------

``void getNextNMessages(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

notifyDownloadedLine
--------------------

``void notifyDownloadedLine(line, key)``

Parameters
^^^^^^^^^^

* in string line
* in nsMsgKey key

notifyFinishedDownloadinghdrs
-----------------------------

``void notifyFinishedDownloadinghdrs()``

getDatabaseWithoutCache
-----------------------

``nsIMsgDatabase getDatabaseWithoutCache()``

Retrieves the database, but does not cache it in mDatabase.

This is useful for operations that shouldn't hold open the database.

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

cancelMessage
-------------

``void cancelMessage(aMsgHdr, aMsgWindow)``

Requests that a message be canceled.

Note that, before sending the news cancel, this method will check to make
sure that the user has proper permission to cancel the message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in :doc:`nsIMsgWindow` aMsgWindow

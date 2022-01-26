==================
nsIMsgProtocolInfo
==================

`mailnews/base/public/nsIMsgProtocolInfo.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgProtocolInfo.idl>`_


Properties
==========

defaultLocalPath
----------------

``attribute nsIFile defaultLocalPath``

the default path to store local data for this type of
server. Each server is usually in a subdirectory below this

serverIID
---------

``readonly attribute nsIIDPtr serverIID``

the IID of the protocol-specific interface for this server
usually used from JS to dynamically get server-specific attributes

requiresUsername
----------------

``readonly attribute boolean requiresUsername``

does this server type require a username?
for instance, news does not but IMAP/POP do

preflightPrettyNameWithEmailAddress
-----------------------------------

``readonly attribute boolean preflightPrettyNameWithEmailAddress``

if the pretty name of the server should
just be the e-mail address. Otherwise it usually
ends up being something like "news on hostname"

canDelete
---------

``readonly attribute boolean canDelete``

can this type of server be removed from the account manager?
for instance, local mail is not removable

canLoginAtStartUp
-----------------

``readonly attribute boolean canLoginAtStartUp``

can this type of server log in at startup?

canDuplicate
------------

``readonly attribute boolean canDuplicate``

can you duplicate this server?
for instance, local mail is unique and should not be duplicated.

canGetMessages
--------------

``readonly attribute boolean canGetMessages``

An attribute that tell us whether on not we can
get messages for the given server type
this is poorly named right now.
it's really is there an inbox for this type?
XXX todo, rename this.

canGetIncomingMessages
----------------------

``readonly attribute boolean canGetIncomingMessages``

do messages arrive for this server
if they do, we can use our junk controls on it.

defaultDoBiff
-------------

``readonly attribute boolean defaultDoBiff``

do biff by default?

showComposeMsgLink
------------------

``readonly attribute boolean showComposeMsgLink``

do we need to show compose message link in the AccountCentral page ?

foldersCreatedAsync
-------------------

``readonly attribute boolean foldersCreatedAsync``

Will new folders be created asynchronously?

Methods
=======

getDefaultServerPort
--------------------

``long getDefaultServerPort(isSecure)``

Parameters
^^^^^^^^^^

* in boolean isSecure

Return value
^^^^^^^^^^^^

* long

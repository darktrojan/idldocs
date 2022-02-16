=============
nsIMsgAccount
=============

`mailnews/base/public/nsIMsgAccount.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgAccount.idl>`_

An account consists of an incoming server and one or more
outgoing identities. An account is identified by a key,
which is the <account> string in the account preferences,
such as in mail.account.<account>.identities.

Properties
==========

key
---

``attribute ACString key``

incomingServer
--------------

``attribute nsIMsgIncomingServer incomingServer``

identities
----------

``readonly attribute Array<nsIMsgIdentity> identities``

defaultIdentity
---------------

``attribute nsIMsgIdentity defaultIdentity``

Methods
=======

addIdentity
-----------

``void addIdentity(identity)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity

removeIdentity
--------------

``void removeIdentity(identity)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity

clearAllValues
--------------

``void clearAllValues()``

toString
--------

``AString toString()``

Return value
^^^^^^^^^^^^

* AString

createServer
------------

``void createServer()``

Create the server, with error returns.

Normally each valid account also has a valid server.

If an extension that creates a server type failed to load, then we
may have an existing account without a valid server. We don't want
to simply delete that account, as that would make the user re-enter
all of the account information after what may be a temporary
update glitch. But we also don't want to leave junk lying around
forever. So what we do is note the time when we first noticed
that the server was unavailable. After a period of time set
in a preference, if the server is still unavailable then delete
the associated account.

Accounts with invalid server are not shown in any way by the account
manager. But if the server becomes available (for example if an extension
is loaded), then the account will reappear when accounts are loaded.

Preference definitions:

mail.server.serverN.secondsToLeaveUnavailable
mail.server.serverN.timeFoundUnavailable

secondsToLeaveUnavailable: is set by the extension to indicate the
delay, in seconds, between first detection that a server is
unavailable, and the time it can be deleted. This should be set
by the extension when the server is created. If missing, treat as 0.
A typical value would be 2592000 (30 days)(24 hr/day)(3600 seconds/hr)

timeFoundUnavailable: is set by core code the first time that a
server is detected as unavailable, using now() converted to seconds.
If that time + secondsToLeaveUnavailable is exceeded, core code may
delete the server and its associated account (though for now we default
to the previous behavior, which is to just delete the account).

Throws
^^^^^^

* NS_ERROR_NOT_AVAILABLE if the server component type could not
  be created
  NS_ERROR_ALREADY_INITIALIZED if the server is already created
  (Other errors may also be possible)

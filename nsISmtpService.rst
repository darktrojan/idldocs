==============
nsISmtpService
==============

`mailnews/compose/public/nsISmtpService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsISmtpService.idl>`_


Properties
==========

servers
-------

``readonly attribute Array<nsISmtpServer> servers``

A copy of the array of SMTP servers, as stored in the preferences

defaultServer
-------------

``attribute nsISmtpServer defaultServer``

The default server, across sessions of the app
(eventually there will be a session default which does not
persist past shutdown)

sessionDefaultServer
--------------------

``attribute nsISmtpServer sessionDefaultServer``

The "session default" server - this is never saved, and only used
for the current session. Always falls back to the default server
unless explicitly set.

Methods
=======

sendMailMessage
---------------

``void sendMailMessage(aFilePath, aRecipients, aSenderIdentity, aSender, aPassword, aUrlListener, aStatusListener, aNotificationCallbacks, aRequestDSN, aMessageId, aURL, aRequest)``

Sends a mail message via the given parameters. This function builds an
SMTP URL and makes an SMTP connection, and then runs the url.
The SMTP server defined
in the aSenderIdentity object (see nsIMsgIdentity) will be used to send
the message. If there is no SMTP server defined in aSenderIdentity, the
default SMTP server will be used.

@note The file to send must be in the format specified by RFC 2822 for
sending data. This includes having the correct CRLF line endings
throughout the file, and the <CRLF>.<CRLF> at the end of the file.
sendMailMessage does no processing/additions on the file.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFilePath
* in string aRecipients
* in :doc:`nsIMsgIdentity` aSenderIdentity
* in string aSender
* in AString aPassword
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgStatusFeedback` aStatusListener
* in :doc:`nsIInterfaceRequestor` aNotificationCallbacks
* in boolean aRequestDSN
* in ACString aMessageId
* out :doc:`nsIURI` aURL
* out :doc:`nsIRequest` aRequest

verifyLogon
-----------

``nsIURI verifyLogon(aServer, aListener, aMsgWindow)``

Verifies that we can logon to the server with given password

Parameters
^^^^^^^^^^

* in :doc:`nsISmtpServer` aServer
* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  - the url that we run.

getServerByIdentity
-------------------

``nsISmtpServer getServerByIdentity(aSenderIdentity)``

Return the SMTP server that is associated with an identity.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aSenderIdentity

  the identity

Return value
^^^^^^^^^^^^

* :doc:`nsISmtpServer`

createServer
------------

``nsISmtpServer createServer()``

Create a new SMTP server.
Use this instead of createInstance(), so that the SMTP Service can
be aware of this server

Return value
^^^^^^^^^^^^

* :doc:`nsISmtpServer`

findServer
----------

``nsISmtpServer findServer(username, hostname)``

Find the first server with the given hostname and/or username.
Note: if either username or hostname is empty, then that parameter will
not be used in the matching process.

Parameters
^^^^^^^^^^

* in string username
* in string hostname

Return value
^^^^^^^^^^^^

* :doc:`nsISmtpServer`

  null if no server is found

getServerByKey
--------------

``nsISmtpServer getServerByKey(key)``

Look up the server with the given key
If the server does not exist, create it and add it to our list

Parameters
^^^^^^^^^^

* in string key

Return value
^^^^^^^^^^^^

* :doc:`nsISmtpServer`

deleteServer
------------

``void deleteServer(server)``

Delete the given server from the server list - does nothing if the server
does not exist

Parameters
^^^^^^^^^^

* in :doc:`nsISmtpServer` server

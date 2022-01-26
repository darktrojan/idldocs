=============
nsISmtpServer
=============

`mailnews/compose/public/nsISmtpServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsISmtpServer.idl>`_

This interface represents a single SMTP Server. A SMTP server instance may be
created/obtained from nsIMsgAccountManager.

Most of the attributes will set/get preferences from the main preferences
file.

Properties
==========

key
---

``attribute string key``

description
-----------

``attribute AUTF8String description``

hostname
--------

``attribute AUTF8String hostname``

port
----

``attribute int32_t port``

username
--------

``attribute ACString username``

clientid
--------

``attribute ACString clientid``

The CLIENTID to use for this server (if required).
@see https://tools.ietf.org/html/draft-storey-smtp-client-id-05

clientidEnabled
---------------

``attribute boolean clientidEnabled``

Whether the CLIENTID feature above is enabled.

password
--------

``attribute AString password``

The password to access the server with (if required).

@note this is stored within the server instance but not within preferences.
It can be specified/saved here to avoid prompting the user constantly for
the sending password.

displayname
-----------

``readonly attribute string displayname``

authMethod
----------

``attribute nsMsgAuthMethodValue authMethod``

Authentication mechanism.

@see nsMsgAuthMethod (in MailNewsTypes2.idl)
Same as "mail.smtpserver...authMethod" pref

Compatibility note: This attribute had a different meaning in TB < 3.1

socketType
----------

``attribute nsMsgSocketTypeValue socketType``

Whether to SSL or STARTTLS or not

@see nsMsgSocketType (in MailNewsTypes2.idl)
Same as "mail.smtpserver...try_ssl" pref

helloArgument
-------------

``readonly attribute ACString helloArgument``

May contain an alternative argument to EHLO or HELO to provide to the
server. Reflects the value of the mail.smtpserver.*.hello_argument pref.
This is mainly useful where ISPs don't bother providing PTR records for
their servers and therefore users get an error on sending. See bug 244030
for more discussion.

serverURI
---------

``readonly attribute AUTF8String serverURI``

Methods
=======

getPasswordWithUI
-----------------

``AString getPasswordWithUI(promptString, promptTitle, netPrompt)``

Gets a password for this server, using a UI prompt if necessary.

Parameters
^^^^^^^^^^

* in wstring promptString
* in wstring promptTitle
* in :doc:`nsIAuthPrompt` netPrompt

Return value
^^^^^^^^^^^^

* AString

  The password to use (may be null if no password was
  obtained).

getUsernamePasswordWithUI
-------------------------

``void getUsernamePasswordWithUI(promptString, promptTitle, netPrompt, userid, password)``

Gets a username and password for this server, using a UI prompt if
necessary.

Parameters
^^^^^^^^^^

* in wstring promptString
* in wstring promptTitle
* in :doc:`nsIAuthPrompt` netPrompt
* out ACString userid
* out AString password

forgetPassword
--------------

``void forgetPassword()``

Calling this will *remove* the saved password for this server from the
password manager and from the stored value.

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

clearAllValues
--------------

``void clearAllValues()``

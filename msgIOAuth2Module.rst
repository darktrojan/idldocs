================
msgIOAuth2Module
================

`mailnews/base/public/msgIOAuth2Module.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/msgIOAuth2Module.idl>`_

An interface for managing the responsibilities of using OAuth2 to produce a
bearer token, for use in SASL steps.

Methods
=======

initFromSmtp
------------

``bool initFromSmtp(aSmtpServer)``

Initialize the OAuth2 parameters from an SMTP server, and return whether or
not we can authenticate with OAuth2.

Parameters
^^^^^^^^^^

* in :doc:`nsISmtpServer` aSmtpServer

Return value
^^^^^^^^^^^^

* bool

initFromMail
------------

``bool initFromMail(aServer)``

Initialize the OAuth2 parameters from an incoming server, and return
whether or not we can authenticate with OAuth2.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` aServer

Return value
^^^^^^^^^^^^

* bool

connect
-------

``void connect(aWithUI, aCallback)``

Connect to the OAuth2 server to get an access token.

Parameters
^^^^^^^^^^

* in boolean aWithUI
* in msgIOAuth2ModuleListener aCallback

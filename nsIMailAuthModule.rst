=================
nsIMailAuthModule
=================

`mailnews/base/public/nsIMailAuthModule.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMailAuthModule.idl>`_

nsIAuthModule provides GSSAPI, NTLM authentications, but it is not
scriptable. nsIMailAuthModule wraps nsIAuthModule and makes it easy to use in
JavaScript.

The contract id is: "@mozilla.org/mail/auth-module;1".

@see nsIAuthModule

Methods
=======

init
----

``void init(aType, aServiceName, aServiceFlags, aDomain, aUsername, aPassword)``

Initialize an auth module. This is a combination of
nsIAuthModule::CreateInstance and nsIAuthModule::Init. The aType argument
is passed to CreateInstance, other arguments are passed to Init.

Parameters
^^^^^^^^^^

* in string aType
* in ACString aServiceName
* in unsigned long aServiceFlags
* in AString aDomain
* in AString aUsername
* in AString aPassword

getNextToken
------------

``ACString getNextToken(aInToken)``

Get the next token in a sequence of authentication steps.

Parameters
^^^^^^^^^^

* in ACString aInToken

Return value
^^^^^^^^^^^^

* ACString

  @returns
  A base64 encoded string, usually a response to a server challenge.

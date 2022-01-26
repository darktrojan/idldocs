========================
msgIOAuth2ModuleListener
========================

`mailnews/base/public/msgIOAuth2Module.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/msgIOAuth2Module.idl>`_

A listener callback for OAuth2 SASL authentication. This would be represented
as a promise, but this needs to be consumed by C++ code.

Methods
=======

onSuccess
---------

``void onSuccess(aBearerToken)``

Called on successful OAuth2 authentication with the base64-encoded
string to send as the client initial response for SASL XOAUTH2.

Parameters
^^^^^^^^^^

* in ACString aBearerToken

onFailure
---------

``void onFailure(aError)``

Parameters
^^^^^^^^^^

* in nsresult aError

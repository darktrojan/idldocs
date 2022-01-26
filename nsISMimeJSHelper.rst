================
nsISMimeJSHelper
================

`mailnews/extensions/smime/nsISMimeJSHelper.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsISMimeJSHelper.idl>`_


Methods
=======

getRecipientCertsInfo
---------------------

``void getRecipientCertsInfo(compFields, emailAddresses, certIssuedInfos, certExpiresInfos, certs, canEncrypt)``

Obtains detailed information about the certificate availability
status of email recipients.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgCompFields` compFields
* out Array<AString> emailAddresses
* out Array<AString> certIssuedInfos
* out Array<AString> certExpiresInfos
* out Array<:doc:`nsIX509Cert`> certs
* out boolean canEncrypt

getNoCertAddresses
------------------

``Array<AString> getNoCertAddresses(compFields)``

Obtains a list of email addresses where valid email recipient certificates
are not yet available.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgCompFields` compFields

Return value
^^^^^^^^^^^^

* Array<AString>

  The list of email addresses without valid certs

=========
msgIJaUrl
=========

`mailnews/jsaccount/public/msgIJaUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/jsaccount/public/msgIJaUrl.idl>`_

Additional interface supported by JsBaseUrl to allow setting variables that
are typically done in C++ by overriding classes, which is not allowed in JS.

Methods
=======

setUrlType
----------

``void setUrlType(type)``

Set the URL type, which will be checked by nsIMsgMailNewsUrl::IsUrlType. See
IsUrlType for possible values.

Parameters
^^^^^^^^^^

* in unsigned long type

setSpec
-------

``void setSpec(spec)``

Set the spec on a URL.

Parameters
^^^^^^^^^^

* in AUTF8String spec

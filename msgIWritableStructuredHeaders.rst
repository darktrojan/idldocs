=============================
msgIWritableStructuredHeaders
=============================

`mailnews/mime/public/msgIStructuredHeaders.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/msgIStructuredHeaders.idl>`_

An interface that enhances msgIStructuredHeaders by allowing the values of
headers to be modified.

Methods
=======

setHeader
---------

``void setHeader(aHeaderName, aValue)``

Store the given value for the given header, overwriting any previous value
that was stored for said header.

Parameters
^^^^^^^^^^

* in string aHeaderName
* in jsval aValue

deleteHeader
------------

``void deleteHeader(aHeaderName)``

Forget any previous value that was stored for the given header.

Parameters
^^^^^^^^^^

* in string aHeaderName

addAllHeaders
-------------

``void addAllHeaders(aOtherHeaders)``

Copy all of the structured values from another set of structured headers to
the current one, overwriting any values that may have been specified
locally. Note that the copy is a shallow copy of the value.

Parameters
^^^^^^^^^^

* in msgIStructuredHeaders aOtherHeaders

setUnstructuredHeader
---------------------

``void setUnstructuredHeader(aHeaderName, aValue)``

Set the value of the header as if it were an unstructured header. Such
headers include most notably the Subject header.

Parameters
^^^^^^^^^^

* in string aHeaderName
* in AString aValue

setAddressingHeader
-------------------

``void setAddressingHeader(aHeaderName, aAddresses)``

Set the value of the header as if it were an addressing header, such as the
From or To headers.

Parameters
^^^^^^^^^^

* in string aHeaderName
* in Array<msgIAddressObject> aAddresses

setRawHeader
------------

``void setRawHeader(aHeaderName, aValue)``

Store the value of the header using a raw version as would be represented
in MIME.

Parameters
^^^^^^^^^^

* in string aHeaderName
* in AUTF8String aValue

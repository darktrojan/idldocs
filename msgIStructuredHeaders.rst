=====================
msgIStructuredHeaders
=====================

`mailnews/mime/public/msgIStructuredHeaders.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/msgIStructuredHeaders.idl>`_

A collection of MIME headers that are stored in a rich, structured format.

The structured forms defined in this method use the structured decoder and
encoder functionality found in jsmime to interconvert between the raw string
forms found in the actual message text and the structured forms supported by
this interface. Extensions can register their own custom structured headers
by listing the source URL of their code under the category
"custom-mime-encoder".

The alternative modes of access for specific headers are expected to only
work for the headers for which that mode of access is the correct one. For
example, retrieving the "To" header from getUnstructuredHeader would fail,
since the To header is not an unstructured header but an addressing header.
They are provided mostly as a convenience to C++ which is much less able to
utilize a fully generic format.

With the exception of mismatched headers, the methods do not throw an
exception if the header is missing but rather return an appropriate default
value as indicated in their documentation.

Properties
==========

headerNames
-----------

``readonly attribute nsIUTF8StringEnumerator headerNames``

Retrieve an enumerator of the names of all headers in this set of headers.
The header names returned may be in different cases depending on the
precise implementation of this interface, so implementations should not
rely on an exact kind of case being returned.

Methods
=======

getHeader
---------

``jsval getHeader(aHeaderName)``

Retrieve the value of the header stored in this set of headers. If the
header is not present, then undefined is returned.

Parameters
^^^^^^^^^^

* in string aHeaderName

Return value
^^^^^^^^^^^^

* jsval

hasHeader
---------

``bool hasHeader(aHeaderName)``

Return true if and only if the given header is already set.

Parameters
^^^^^^^^^^

* in string aHeaderName

Return value
^^^^^^^^^^^^

* bool

getUnstructuredHeader
---------------------

``AString getUnstructuredHeader(aHeaderName)``

Retrieve the value of the header as if it is an unstructured header. Such
headers include most notably the Subject header. If the header is not
present, then null is returned. This is reflected in C++ as an empty string
with IsVoid() set to true (distinguishing it from a header that is present
but contains an empty string).

Parameters
^^^^^^^^^^

* in string aHeaderName

Return value
^^^^^^^^^^^^

* AString

getAddressingHeader
-------------------

``Array<msgIAddressObject> getAddressingHeader(aHeaderName, aPreserveGroups)``

Retrieve the value of the header if it is an addressing header, such as the
From or To headers. If the header is not present, then an empty array is
returned.

Parameters
^^^^^^^^^^

* in string aHeaderName
* in boolean aPreserveGroups

Return value
^^^^^^^^^^^^

* Array<msgIAddressObject>

getRawHeader
------------

``AUTF8String getRawHeader(aHeaderName)``

Retrieve a raw version of the header value as would be represented in MIME.
This form does not include the header name and colon, trailing whitespace,
nor embedded CRLF pairs in the case of very long header names.

Parameters
^^^^^^^^^^

* in string aHeaderName

Return value
^^^^^^^^^^^^

* AUTF8String

buildMimeText
-------------

``AUTF8String buildMimeText(sanitizeDate)``

Retrieve the MIME representation of all of the headers.
The header values are emitted in an ASCII form, unless internationalized
email addresses are involved. The extra CRLF indicating the end of headers
is not included in this representation.
This accessor is provided mainly for the benefit of C++ consumers of this
interface, since the JSMime headeremitter functionality allows more
fine-grained customization of the results.

Parameters
^^^^^^^^^^

* in boolean sanitizeDate

Return value
^^^^^^^^^^^^

* AUTF8String

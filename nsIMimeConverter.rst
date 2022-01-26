================
nsIMimeConverter
================

`mailnews/mime/public/nsIMimeConverter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeConverter.idl>`_

Encode/decode mail headers (via libmime).

Constants
=========

MIME_ENCODED_WORD_SIZE
----------------------

**Type**: ``long``

**Value**: ``72``

Suggested byte length limit for use when calling encodeMimePartIIStr_UTF8.

MAX_CHARSET_NAME_LENGTH
-----------------------

**Type**: ``long``

**Value**: ``64``


Methods
=======

encodeMimePartIIStr_UTF8
------------------------

``AUTF8String encodeMimePartIIStr_UTF8(aHeader, aAddressingHeader, aFieldNameLen, aMaxLineLen)``

Encode a UTF-8 string into a form containing only ASCII characters using
RFC 2047 encoded words where necessary.

Parameters
^^^^^^^^^^

* in AUTF8String aHeader
* in boolean aAddressingHeader
* in long aFieldNameLen
* in long aMaxLineLen

Return value
^^^^^^^^^^^^

* AUTF8String

  The encoded header.

decodeMimeHeaderToUTF8
----------------------

``AUTF8String decodeMimeHeaderToUTF8(header, default_charset, override_charset, eatContinuations)``

Decode a MIME header to UTF-8 if conversion is required.  Marked as
noscript because the return value may contain non-ASCII characters.

Parameters
^^^^^^^^^^

* in ACString header
* in string default_charset
* in boolean override_charset
* in boolean eatContinuations

Return value
^^^^^^^^^^^^

* AUTF8String

  UTF-8 encoded value if conversion was required, nullptr if no
  conversion was required.

decodeMimeHeader
----------------

``AString decodeMimeHeader(header, default_charset, override_charset, eatContinuations)``

Decode a MIME header to UTF-16.

Parameters
^^^^^^^^^^

* in string header
* in string default_charset
* in boolean override_charset
* in boolean eatContinuations

Return value
^^^^^^^^^^^^

* AString

  UTF-16 encoded value as an AString.

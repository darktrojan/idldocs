==========================
nsICharsetConverterManager
==========================

`mailnews/intl/nsICharsetConverterManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/intl/nsICharsetConverterManager.idl>`_


Methods
=======

getCharsetAlias
---------------

``ACString getCharsetAlias(aCharset)``

A shortcut to calling nsICharsetAlias to do alias resolution

Parameters
^^^^^^^^^^

* in string aCharset

Return value
^^^^^^^^^^^^

* ACString

Throws
^^^^^^

* if aCharset is an unknown charset.

getCharsetTitle
---------------

``AString getCharsetTitle(aCharset)``

Get the human-readable name for the given charset.

Parameters
^^^^^^^^^^

* in string aCharset

Return value
^^^^^^^^^^^^

* AString

Throws
^^^^^^

* if aCharset is an unknown charset.

getCharsetData
--------------

``AString getCharsetData(aCharset, aProp)``

Get some data about the given charset. This includes whether the
character encoding may be used for certain purposes, if it is
multi-byte, and the language code for it. See charsetData.properties
for the source of this data. Some known property names:
LangGroup      - language code for charset, e.g. 'he' and 'zh-CN'.
isMultibyte    - is this a multi-byte charset?
isInternal     - not to be used in untrusted web content.

Parameters
^^^^^^^^^^

* in string aCharset
* in wstring aProp

Return value
^^^^^^^^^^^^

* AString

  the value of the property, for the character encoding.

Throws
^^^^^^

* if aCharset is an unknown charset.

getCharsetLangGroup
-------------------

``AUTF8String getCharsetLangGroup(aCharset)``

Get the language group for the given charset. This is similar to
calling <tt>getCharsetData</tt> with the <tt>prop</tt> "LangGroup".

Parameters
^^^^^^^^^^

* in string aCharset

Return value
^^^^^^^^^^^^

* AUTF8String

  the language code for the character encoding.

Throws
^^^^^^

* if aCharset is an unknown charset.

getCharsetLangGroupRaw
----------------------

``AUTF8String getCharsetLangGroupRaw(aCharset)``

Parameters
^^^^^^^^^^

* in string aCharset

Return value
^^^^^^^^^^^^

* AUTF8String

utf7ToUnicode
-------------

``AString utf7ToUnicode(aMutf7)``

Decoding of UTF-7 in message headers and bodies.

Parameters
^^^^^^^^^^

* in ACString aMutf7

Return value
^^^^^^^^^^^^

* AString

mutf7ToUnicode
--------------

``AString mutf7ToUnicode(aMutf7)``

Support for Modified UTF-7 (MUTF-7) used by IMAP.

Parameters
^^^^^^^^^^

* in ACString aMutf7

Return value
^^^^^^^^^^^^

* AString

unicodeToMutf7
--------------

``ACString unicodeToMutf7(aUnicode)``

Parameters
^^^^^^^^^^

* in AString aUnicode

Return value
^^^^^^^^^^^^

* ACString

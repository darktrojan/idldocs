==================
nsIMsgHeaderParser
==================

`mailnews/mime/public/nsIMsgHeaderParser.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMsgHeaderParser.idl>`_

A utility service for manipulating addressing headers in email messages.

This interface is designed primarily for use from JavaScript code; code in
C++ should use the methods in MimeHeaderParser.h instead, as it is better
designed to take advantage of C++'s features, particularly with respect to
arrays.

There are two methods for parsing MIME headers, one for RFC 2047-decoded
strings, and one for non-RFC 2047-decoded strings.

In general, this API attempts to preserve the format of addresses as
faithfully as possible. No case normalization is performed at any point.
However, internationalized email addresses generally need extra processing to
work properly, so while this API should handle them without issues, consumers
of this API may fail to work properly when presented with such addresses. To
ease use for such cases, future versions of the API may incorporate necessary
normalization steps to make oblivious consumers more likely to work properly.

Methods
=======

parseEncodedHeader
------------------

``Array<msgIAddressObject> parseEncodedHeader(aEncodedHeader, aHeaderCharset, aPreserveGroups)``

Parse an address-based header that has not yet been 2047-decoded.

The result of this method is an array of objects described in the above
comment. Note that the header is a binary string that will be decoded as if
passed into nsIMimeConverter.

Parameters
^^^^^^^^^^

* in ACString aEncodedHeader
* in string aHeaderCharset
* in bool aPreserveGroups

Return value
^^^^^^^^^^^^

* Array<msgIAddressObject>

  An array corresponding to the header description.

parseEncodedHeaderW
-------------------

``Array<msgIAddressObject> parseEncodedHeaderW(aEncodedHeader)``

Parse an address-based header that has not yet been 2047-decoded and does not
contain raw octets but instead wide (UTF-16) characters.

Parameters
^^^^^^^^^^

* in AString aEncodedHeader

Return value
^^^^^^^^^^^^

* Array<msgIAddressObject>

  An array corresponding to the header description.

parseDecodedHeader
------------------

``Array<msgIAddressObject> parseDecodedHeader(aDecodedHeader, aPreserveGroups)``

Parse an address-based header that has been 2047-decoded.

The result of this method is an array of objects described in the above
comment. Note that the header is a binary string that will be decoded as if
passed into nsIMimeConverter.

Parameters
^^^^^^^^^^

* in AString aDecodedHeader
* in bool aPreserveGroups

Return value
^^^^^^^^^^^^

* Array<msgIAddressObject>

  An array corresponding to the header description.

makeMimeHeader
--------------

``AString makeMimeHeader(aAddresses)``

Given an array of addresses, make a MIME header suitable for emission.

The return value of this method is not directly suitable for use in a MIME
message but rather needs to be passed through nsIMimeConverter first to
have RFC-2047 encoding applied and the resulting output wrapped to adhere
to maximum line length formats.

Parameters
^^^^^^^^^^

* in Array<msgIAddressObject> aAddresses

Return value
^^^^^^^^^^^^

* AString

  A string that is suitable for writing in a MIME message.

extractFirstName
----------------

``AString extractFirstName(aDecodedHeader)``

Return the first address in the list in a format suitable for display.

This is largely a convenience method for handling From headers (or similar),
which are expected to only have a single element in them. It is exactly
equivalent to saying (parseDecodedHeader(decodedHeader))[0].toString().

Parameters
^^^^^^^^^^

* in AString aDecodedHeader

Return value
^^^^^^^^^^^^

* AString

  The first address, suitable for display.

removeDuplicateAddresses
------------------------

``AUTF8String removeDuplicateAddresses(aAddrs, aOtherAddrs)``

Returns a copy of the input which may have had some addresses removed.
Addresses are removed if they are already in either of the supplied
address lists.

Addresses are considered to be the same if they contain the same email
part (case-insensitive). Since the email part should never be RFC
2047-encoded, this method should work whether or not the header is
RFC 2047-encoded.

Parameters
^^^^^^^^^^

* in AUTF8String aAddrs
* in AUTF8String aOtherAddrs

Return value
^^^^^^^^^^^^

* AUTF8String

  The original header with duplicate addresses removed.

makeMailboxObject
-----------------

``msgIAddressObject makeMailboxObject(aName, aEmail)``

Parameters
^^^^^^^^^^

* in AString aName
* in AString aEmail

Return value
^^^^^^^^^^^^

* msgIAddressObject

makeGroupObject
---------------

``msgIAddressObject makeGroupObject(aName, aMembers)``

Parameters
^^^^^^^^^^

* in AString aName
* in Array<msgIAddressObject> aMembers

Return value
^^^^^^^^^^^^

* msgIAddressObject

makeFromDisplayAddress
----------------------

``Array<msgIAddressObject> makeFromDisplayAddress(aDisplayAddresses)``

Return an array of structured mailbox objects for the given display name
string.

The string is expected to be a comma-separated sequence of strings that
would be produced by msgIAddressObject::toString(). For example, the string
"Bond, James <agent007@mi5.invalid>" would produce one address object,
while the string "webmaster@nowhere.invalid, child@nowhere.invalid" would
produce two address objects.

Parameters
^^^^^^^^^^

* in AString aDisplayAddresses

Return value
^^^^^^^^^^^^

* Array<msgIAddressObject>

extractHeaderAddressMailboxes
-----------------------------

``ACString extractHeaderAddressMailboxes(aLine)``

Given a string which contains a list of Header addresses, returns a
comma-separated list of just the `mailbox' portions.

Parameters
^^^^^^^^^^

* in ACString aLine

Return value
^^^^^^^^^^^^

* ACString

  A comma-separated list of just the mailbox parts
  of the email-addresses.

makeMimeAddress
---------------

``AString makeMimeAddress(aName, aEmail)``

Given a name and email address, produce a string that is suitable for
emitting in a MIME header (after applying RFC 2047 encoding).

@note This is a temporary method.

Parameters
^^^^^^^^^^

* in AString aName
* in AString aEmail

Return value
^^^^^^^^^^^^

* AString

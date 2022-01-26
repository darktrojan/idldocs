=================
msgIAddressObject
=================

`mailnews/mime/public/nsIMsgHeaderParser.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMsgHeaderParser.idl>`_

A structured representation of an address.

This is meant to correspond to the address production from RFC 5322. As a
result, an instance of this interface is either a single mailbox or a group
of mailboxes. The difference between the two forms is in which attribute is
undefined: mailboxes leave the members attribute undefined while groups leave
the email attribute undefined.

For example, an address like "John Doe <jdoe@machine.example>" will, when
parsed, result in an instance with the name attribute set to "John Doe", the
email attribute set to "jdoe@machine.example", and the members variable left
undefined.

A group like "undisclosed-recipients:;" will, when parsed, result in an
instance with the name attribute set to "undisclosed-recipients", the email
attribute left defined, and the members variable set to an empty array.

In general, the attributes of this interface are always meant to be in a form
suitable for display purposes, and not in a form usable for MIME emission. In
particular, email addresses could be fully internationalized and non-ASCII,
RFC 2047-encoded words may appear in names, and the name or email parameters
are unquoted.

Properties
==========

name
----

``readonly attribute AString name``

email
-----

``readonly attribute AString email``

group
-----

``readonly attribute jsval group``

The member mailboxes of this group, which may be an empty list.

Due to the limitations of XPIDL, the type of this attribute cannot be
properly reflected. It is actually an array of msgIAddressObject instances,
although it is instead undefined if this object does not represent a group.

Methods
=======

toString
--------

``AString toString()``

Return value
^^^^^^^^^^^^

* AString

==================
nsIMsgAttachedFile
==================

`mailnews/compose/public/nsIMsgSend.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSend.idl>`_

When we have downloaded a URL to a tmp file for attaching, this
represents everything we learned about it (and did to it) in the
process.

Properties
==========

origUrl
-------

``attribute nsIURI origUrl``

tmpFile
-------

``attribute nsIFile tmpFile``

type
----

``attribute ACString type``

encoding
--------

``attribute ACString encoding``

The encoding of the tmp file. This will be set only if the original
document had an encoding already; we don't do base64 encoding and so forth
until it's time to assemble a full MIME message of all parts.

description
-----------

``attribute ACString description``

cloudPartInfo
-------------

``attribute ACString cloudPartInfo``

xMacType
--------

``attribute ACString xMacType``

xMacCreator
-----------

``attribute ACString xMacCreator``

realName
--------

``attribute ACString realName``

size
----

``attribute unsigned long size``

Some statistics about the data that was written to the file, so that when
it comes time to compose a MIME message, we can make an informed decision
about what Content-Transfer-Encoding would be best for this attachment.
(If it's encoded already, we ignore this information and ship it as-is.)

unprintableCount
----------------

``attribute unsigned long unprintableCount``

highbitCount
------------

``attribute unsigned long highbitCount``

ctlCount
--------

``attribute unsigned long ctlCount``

nullCount
---------

``attribute unsigned long nullCount``

maxLineLength
-------------

``attribute unsigned long maxLineLength``

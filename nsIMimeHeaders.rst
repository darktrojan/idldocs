==============
nsIMimeHeaders
==============

`mailnews/mime/public/nsIMimeHeaders.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeHeaders.idl>`_

An interface that can extract individual headers from a body of headers.

Properties
==========

allHeaders
----------

``readonly attribute ACString allHeaders``

The current text of all header data.

Unlike the asMimeText property, this result preserves the original
representation of the header text, including alternative line endings or
custom, non-8-bit text. For instances of this interface, this attribute is
usually preferable to asMimeText.

Methods
=======

initialize
----------

``void initialize(allHeaders)``

Parameters
^^^^^^^^^^

* in ACString allHeaders

extractHeader
-------------

``ACString extractHeader(headerName, getAllOfThem)``

Get the text of a header.

Leading and trailing whitespace from headers will be stripped from the
return value. If getAllOfThem is set to true, then the returned string will
have all of the values of the header, in order, joined with the ',\r\n\t'.

If the header is not present, then the returned value is NULL.

Parameters
^^^^^^^^^^

* in string headerName
* in boolean getAllOfThem

Return value
^^^^^^^^^^^^

* ACString

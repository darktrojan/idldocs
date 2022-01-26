===============
nsICMSDecoderJS
===============

`mailnews/extensions/smime/nsICMSDecoderJS.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/smime/nsICMSDecoderJS.idl>`_

nsICMSDecoderJS
Interface to decode a CMS message, can be called from JavaScript.

Methods
=======

decrypt
-------

``Array<uint8_t> decrypt(input)``

Return the result of decoding/decrypting the given CMS message.

Parameters
^^^^^^^^^^

* in Array<uint8_t> input

Return value
^^^^^^^^^^^^

* Array<uint8_t>

  The decoded data

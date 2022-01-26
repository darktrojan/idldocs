=============
nsIJSIterator
=============

`mailnews/base/public/nsIMsgEnumerator.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgEnumerator.idl>`_

nsIJSIterator implements the JavaScript iterator protocol.
For details on the JS side, see:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterator_protocol

Methods
=======

next
----

``jsval next()``

Return value
^^^^^^^^^^^^

* jsval

  the iteration state.
  'value' holds the next item, and 'done' flags the end of the iteration.
  (notionally, both 'value' and 'done' are always present, but a missing
  'done' is considered to be false, and 'value' should be ignored if
  'done' is true, according to the protocol).

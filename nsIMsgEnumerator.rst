================
nsIMsgEnumerator
================

`mailnews/base/public/nsIMsgEnumerator.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgEnumerator.idl>`_

nsIMsgEnumerator is an object for iterating forward over an ordered set of
messages (nsIMsgHdrs). There is no provision to reset the iteration.

Methods
=======

iterator
--------

``nsIJSIterator iterator()``

Implements the JavaScript iterable protocol, which allows
for...of constructs and the like.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterable_protocol
NOTE: the nsIMsgEnumerator is "used up" by iterator(), just as it is by
getNext()/hasMoreElements(). So you can only loop over the enumerator once.

Return value
^^^^^^^^^^^^

* :doc:`nsIJSIterator`

hasMoreElements
---------------

``boolean hasMoreElements()``

Called to determine whether or not there are any messages remaining
to be retrived from the enumerator.

Return value
^^^^^^^^^^^^

* boolean

  true if getNext() may be called to fetch a message, or
  false if there are no more messages.

getNext
-------

``nsIMsgDBHdr getNext()``

Called to retrieve the next message in the set.

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

  the next element in the enumeration.

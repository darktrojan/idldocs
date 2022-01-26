=======================
nsIAbAutoCompleteResult
=======================

`mailnews/addrbook/public/nsIAbAutoCompleteResult.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbAutoCompleteResult.idl>`_

This interface is used to extend the nsIAutoCompleteResult interface to
provide extra facilities for obtaining more details of the results of
an address book search.

Properties
==========

modelQuery
----------

``attribute AString modelQuery``

The template used to build the query for this search. Optional.

asyncDirectories
----------------

``attribute Array<nsIAbDirectory> asyncDirectories``

Asynchronous address books that were unable to return full results.
This means that they need to be requeried rather than simply filtered.

Methods
=======

getCardAt
---------

``nsIAbCard getCardAt(index)``

Get the card from the result at the given index

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

getEmailToUse
-------------

``AString getEmailToUse(index)``

Gets the email to use for the card within the result at the given index.
This is the email that was matched against for the card where there are
multiple email addresses on a card.

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* AString

  The email address to use from the card.

isCompleteResult
----------------

``bool isCompleteResult(index)``

Indicates whether the source that returned this result returned a
complete result for the query. If true, refining the search will not
trigger a new query, instead simply filtering the previous results.
If false, the directory will be present in asyncDirectories.

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* bool

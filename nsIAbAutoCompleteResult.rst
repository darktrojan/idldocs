=======================
nsIAbAutoCompleteResult
=======================

This interface is used to extend the nsIAutoCompleteResult interface to
provide extra facilities for obtaining more details of the results of
an address book search.

Methods
=======

getCardAt
---------

Get the card from the result at the given index

Parameters
^^^^^^^^^^

* ``in long index``

Return value
^^^^^^^^^^^^

* ``nsIAbCard``

getEmailToUse
-------------

Gets the email to use for the card within the result at the given index.
This is the email that was matched against for the card where there are
multiple email addresses on a card.

@param index  Index of the autocomplete result to return the value for.
@result       The email address to use from the card.

Parameters
^^^^^^^^^^

* ``in long index``

Return value
^^^^^^^^^^^^

* ``AString``

isCompleteResult
----------------

Indicates whether the source that returned this result returned a
complete result for the query. If true, refining the search will not
trigger a new query, instead simply filtering the previous results.
If false, the directory will be present in asyncDirectories.

Parameters
^^^^^^^^^^

* ``in long index``

Return value
^^^^^^^^^^^^

* ``bool``

==================
nsIMsgVCardService
==================


Methods
=======

vCardToAbCard
-------------

``nsIAbCard vCardToAbCard(vCardStr)``

Translates a vCard string into a nsIAbCard.

Parameters
^^^^^^^^^^

* in AString vCardStr

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

  - A card containing the translated vCard data.

escapedVCardToAbCard
--------------------

``nsIAbCard escapedVCardToAbCard(escapedVCardStr)``

Translates an URL-encoded vCard string into a nsIAbCard.

Parameters
^^^^^^^^^^

* in AString escapedVCardStr

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

  - A card containing the translated vCard data.

abCardToEscapedVCard
--------------------

``AString abCardToEscapedVCard(abCard)``

Translates a nsIAbCard into an URL-encoded vCard.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` abCard

Return value
^^^^^^^^^^^^

* AString

  - The string containing the vCard data.

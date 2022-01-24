==================
nsIMsgVCardService
==================


Methods
=======

vCardToAbCard
-------------

Translates a vCard string into a nsIAbCard.

Parameters
^^^^^^^^^^

* ``in AString vCardStr``

Return value
^^^^^^^^^^^^

* ``nsIAbCard``
  - A card containing the translated vCard data.

escapedVCardToAbCard
--------------------

Translates an URL-encoded vCard string into a nsIAbCard.

Parameters
^^^^^^^^^^

* ``in AString escapedVCardStr``

Return value
^^^^^^^^^^^^

* ``nsIAbCard``
  - A card containing the translated vCard data.

abCardToEscapedVCard
--------------------

Translates a nsIAbCard into an URL-encoded vCard.

Parameters
^^^^^^^^^^

* ``in nsIAbCard abCard``

Return value
^^^^^^^^^^^^

* ``AString``
  - The string containing the vCard data.

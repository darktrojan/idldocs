==================
nsIMsgVCardService
==================


Methods
=======

vCardToAbCard
-------------

Translates a vCard string into a nsIAbCard.

@param vCardStr - The string containing the vCard data.
@return - A card containing the translated vCard data.

Parameters
^^^^^^^^^^

* ``in AString vCardStr``

Return value
^^^^^^^^^^^^

* ``nsIAbCard``

escapedVCardToAbCard
--------------------

Translates an URL-encoded vCard string into a nsIAbCard.

@param escapedVCardStr - The string containing the vCard data.
@return - A card containing the translated vCard data.

Parameters
^^^^^^^^^^

* ``in AString escapedVCardStr``

Return value
^^^^^^^^^^^^

* ``nsIAbCard``

abCardToEscapedVCard
--------------------

Translates a nsIAbCard into an URL-encoded vCard.

@param abCard - A card to be translated.
@return - The string containing the vCard data.

Parameters
^^^^^^^^^^

* ``in nsIAbCard abCard``

Return value
^^^^^^^^^^^^

* ``AString``

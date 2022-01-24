=========
nsIAbCard
=========

An interface representing an address book card.

None of these IDs will be reflected in the property collection. Neither
nsIAbCard::properties, nsIAbCard::deleteProperty, nor any of the property
getters and setters are able to interact with these properties.

Fundamentally, a card is a collection of properties. Modifying a property in
some way on a card does not change the backend used to store the card; the
directory is required to do make the changes here.

The following are the core properties that are used:
- Names:
- FirstName, LastName
- PhoneticFirstName, PhoneticLastName
- DisplayName, NickName
- SpouseName, FamilyName
- PrimaryEmail, SecondEmail
- Home Contact:
- HomeAddress, HomeAddress2, HomeCity, HomeState, HomeZipCode, HomeCountry
- HomePhone, HomePhoneType
- Work contact. Same as home, but with `Work' instead of `Home'
- Other Contact:
- FaxNumber, FaxNumberType
- PagerNumber, PagerNumberType
- CellularNumber, CellularNumberType
- JobTitle, Department, Company
- _AimScreenName
- Dates:
- AnniversaryYear, AnniversaryMonth, AnniversaryDay
- BirthYear, BirthMonth, BirthDay
- WebPage1 (work), WebPage2 (home)
- Custom1, Custom2, Custom3, Custom4
- Notes
- Integral properties:
- LastModifiedDate
- PopularityIndex
- PreferMailFormat (see nsIAbPreferMailFormat)
- Photo properties:
- PhotoName
- PhotoType
- PhotoURI

The contract id for the standard implementation is
<tt>\@mozilla.org/addressbook/cardproperty;1</tt>.

Constants
=========

GENERATE_DISPLAY_NAME
---------------------

**Type**: ``unsigned long``

**Value**: ``0``

@{
These constants reflect the possible values of the
mail.addr_book.lastnamefirst preferences. They are intended to be used in
generateName, defined below.

GENERATE_LAST_FIRST_ORDER
-------------------------

**Type**: ``unsigned long``

**Value**: ``1``


GENERATE_FIRST_LAST_ORDER
-------------------------

**Type**: ``unsigned long``

**Value**: ``2``


Methods
=======

generateName
------------

@} */
Generate a name from the item for display purposes.
If this item is an nsIAbCard, then it will use the aGenerateFormat option
to determine the string to return.
If this item is not an nsIAbCard, then the aGenerateFormat option may be
ignored, and the displayName of the item returned.

Parameters
^^^^^^^^^^

* ``in long aGenerateFormat``
  The format to generate as per the GENERATE_*
  constants above.
* ``in nsIStringBundle aBundle``
  An optional parameter that is a pointer to a string
  bundle that holds:
  chrome://messenger/locale/addressbook/addressBook.properties
  If this bundle is not supplied, then the function
  will obtain the bundle itself. If cached by the
  caller and supplied to this function, then
  performance will be improved over many calls.

Return value
^^^^^^^^^^^^

* ``AString``
  A string containing the generated name.

getProperty
-----------

Returns a property for the given name.
@exception NS_ERROR_NOT_AVAILABLE if the named property does not exist.
@exception NS_ERROR_CANNOT_CONVERT_DATA if the property cannot be converted
to the desired type.

Parameters
^^^^^^^^^^

* ``in AUTF8String name``
* ``in nsIVariant defaultValue``

Return value
^^^^^^^^^^^^

* ``nsIVariant``

getPropertyAsAString
--------------------

@{
Returns a property for the given name.  Javascript callers should NOT use these,
but use getProperty instead. XPConnect will do the type conversion automagically.
These functions convert values in the same manner as the default
implementation of nsIVariant. Of particular note is that boolean variables
are converted to integers as in C/C++ (true is a non-zero value), so that
false will be converted to a string of "0" and not "false."
@exception NS_ERROR_NOT_AVAILABLE if the named property does not exist.
@exception NS_ERROR_CANNOT_CONVERT_DATA if the property cannot be converted
to the desired type.

Parameters
^^^^^^^^^^

* ``in string name``

Return value
^^^^^^^^^^^^

* ``AString``

getPropertyAsAUTF8String
------------------------


Parameters
^^^^^^^^^^

* ``in string name``

Return value
^^^^^^^^^^^^

* ``AUTF8String``

getPropertyAsUint32
-------------------


Parameters
^^^^^^^^^^

* ``in string name``

Return value
^^^^^^^^^^^^

* ``unsigned long``

getPropertyAsBool
-----------------


Parameters
^^^^^^^^^^

* ``in string name``

Return value
^^^^^^^^^^^^

* ``boolean``

setProperty
-----------

@} */
Assigns the given to value to the property of the given name.
Should the property exist, its value will be overwritten. An
implementation may impose additional semantic constraints for certain
properties. However, such constraints might not be checked by this method.
@warning A value MUST be convertible to a string; if this convention is not
followed, consumers of cards may fail unpredictably or return incorrect
results.

Parameters
^^^^^^^^^^

* ``in AUTF8String name``
* ``in nsIVariant value``

Return value
^^^^^^^^^^^^

* ``void``

setPropertyAsAString
--------------------

@{
Sets a property for the given name.  Javascript callers should NOT use these,
but use setProperty instead. XPConnect will do the type conversion automagically.
These functions convert values in the same manner as the default
implementation of nsIVariant.

Parameters
^^^^^^^^^^

* ``in string name``
* ``in AString value``

Return value
^^^^^^^^^^^^

* ``void``

setPropertyAsAUTF8String
------------------------


Parameters
^^^^^^^^^^

* ``in string name``
* ``in AUTF8String value``

Return value
^^^^^^^^^^^^

* ``void``

setPropertyAsUint32
-------------------


Parameters
^^^^^^^^^^

* ``in string name``
* ``in unsigned long value``

Return value
^^^^^^^^^^^^

* ``void``

setPropertyAsBool
-----------------


Parameters
^^^^^^^^^^

* ``in string name``
* ``in boolean value``

Return value
^^^^^^^^^^^^

* ``void``

deleteProperty
--------------

@} */
Deletes the property with the given name.
Some properties may not be deleted. However, the implementation will not
check this constraint at this method. If such a property is deleted, an
error may be thrown when the card is modified at the database level.

Parameters
^^^^^^^^^^

* ``in AUTF8String name``

Return value
^^^^^^^^^^^^

* ``void``

hasEmailAddress
---------------

Determines whether or not a card has the supplied email address in either
of its PrimaryEmail or SecondEmail attributes.
Note: This function is likely to be temporary whilst we work out proper
APIs for multi-valued attributes in bug 118665.

Parameters
^^^^^^^^^^

* ``in AUTF8String aEmailAddress``
  The email address to attempt to match against.

Return value
^^^^^^^^^^^^

* ``boolean``
  True if aEmailAddress matches any of the email
  addresses stored in the card.

translateTo
-----------

Translates a card into a specific format.
The following types are supported:
- base64xml
- xml
- vcard
@exception NS_ERROR_ILLEGAL_VALUE if we do not recognize the type.

Parameters
^^^^^^^^^^

* ``in AUTF8String aType``
  The type of item to translate the card into.

Return value
^^^^^^^^^^^^

* ``AUTF8String``
  A string containing the translated card.

generatePhoneticName
--------------------

Translates a card from the specified format
Generate a phonetic name from the card, using the firstName and lastName
values.

Parameters
^^^^^^^^^^

* ``in boolean aLastNameFirst``
  Set to True to put the last name before the first.

Return value
^^^^^^^^^^^^

* ``AString``
  A string containing the generated phonetic name.

generateChatName
----------------

Generate a chat name from the card, containing the value of the
first non-empty chat field.

Parameters
^^^^^^^^^^


Return value
^^^^^^^^^^^^

* ``AString``
  A string containing the generated chat name.

copy
----

This function will copy all values from one card to another.

Parameters
^^^^^^^^^^

* ``in nsIAbCard aSrcCard``

Return value
^^^^^^^^^^^^

* ``void``

equals
------

Returns true if this card is equal to the other card.
The default implementation defines equal as this card pointing to the
same object as @arg aCard; another implementation defines it as equality of
properties and values.
@warning The exact nature of equality is still undefined, and actual
results may not match theoretical results. Most notably, the code
<tt>a.equals(b) == b.equals(a)</tt> might not return true. In
particular, calling equals on cards from different address books
may return inaccurate results.

Parameters
^^^^^^^^^^

* ``in nsIAbCard aCard``
  The card to compare against.

Return value
^^^^^^^^^^^^

* ``boolean``
  Equality, as defined above.

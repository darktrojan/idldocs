==============
nsIAbDirectory
==============

A top-level address book directory.

Please note that in order to be properly instantiated by nsIAbManager, every
type of nsIAbDirectory must have a contract ID of the form:

@mozilla.org/addressbook/directory;1?type=<AB URI Scheme>

Where AB URI Scheme does not include the ://.  For example, for the
SQLite-based address book, the scheme is "jsaddrbook", so the contract ID for
the SQLite-based address book type is:

@mozilla.org/addressbook/directory;1?type=jsaddrbook

Methods
=======

cardForEmailAddress
-------------------

Returns an address book card for the specified email address if found.
If there are multiple cards with the given email address, this method will
return one of these cards in an implementation-defined manner.
Matching is performed in a case-insensitive manner.
This method performs a synchronous operation. If the collection cannot do
the search in such a manner, then it should throw NS_ERROR_NOT_IMPLEMENTED.
@exception NS_ERROR_NOT_IMPLEMENTED If the collection cannot do this.

Parameters
^^^^^^^^^^

* in AUTF8String emailAddress

  The email address to find in any of the email address
  fields. If emailAddress is empty, the database won't
  be searched and the function will return as if no card
  was found.

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

  An nsIAbCard if one was found, else returns NULL.

getCardFromProperty
-------------------

Returns an address book card for the specified property if found.
If there are multiple cards with the given value for the property, this
method will return one of these cards in an implementation-defined manner.
This method performs a synchronous operation. If the collection cannot do
the search in such a manner, then it should throw NS_ERROR_NOT_IMPLEMENTED.
If the property is not natively a string, it can still be searched for
using the string-encoded value of the property, e.g. "0". See
nsIAbCard::getPropertyAsAUTF8String for more information. Empty values will
return no match, to prevent spurious results.
@exception NS_ERROR_NOT_IMPLEMENTED If the collection cannot do this.

Parameters
^^^^^^^^^^

* in string aProperty

  The property to look for.
* in AUTF8String aValue

  The value to search for.
* in boolean aCaseSensitive

  True if matching should be done case-sensitively.

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

  An nsIAbCard if one was found, else returns NULL.

getCardsFromProperty
--------------------

Returns all address book cards with a specific property matching value
This function is almost identical to getCardFromProperty, with the
exception of returning all cards rather than just the first.

Parameters
^^^^^^^^^^

* in string aProperty

  The property to look for.
* in AUTF8String aValue

  The value to search for.
* in boolean aCaseSensitive

  True if matching should be done case-sensitively.

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIAbCard`>

  The matching nsIAbCard instances.

getMailListFromName
-------------------

Returns the nsIAbDirectory for a mailing list with the specified name.

Parameters
^^^^^^^^^^

* in AString aName

Return value
^^^^^^^^^^^^

* :doc:`nsIAbDirectory`

setUID
------


Parameters
^^^^^^^^^^

* in AUTF8String aUID

search
------

Searches the directory for cards matching query.
The query takes the form:
(BOOL1(FIELD1,OP1,VALUE1)..(FIELDn,OPn,VALUEn)(BOOL2(FIELD1,OP1,VALUE1)...)...)
BOOLn   A boolean operator joining subsequent terms delimited by ().
For possible values see CreateBooleanExpression().
FIELDn  An addressbook card data field.
OPn     An operator for the search term.
For possible values see CreateBooleanConditionString().
VALUEn  The value to be matched in the FIELDn via the OPn operator.
The value must be URL encoded by the caller, if it contains any
special characters including '(' and ')'.

Parameters
^^^^^^^^^^

* in AString query
* in AString searchString
* in :doc:`nsIAbDirSearchListener` listener

init
----

Initializes a directory, pointing to a particular URI.

Parameters
^^^^^^^^^^

* in string aURI

cleanUp
-------

Clean up any database connections or open file handles.
Called at shutdown or if the directory is about to be deleted.

Return value
^^^^^^^^^^^^

* Promise

deleteDirectory
---------------


Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` directory

hasCard
-------


Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` cards

Return value
^^^^^^^^^^^^

* boolean

hasDirectory
------------


Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` dir

Return value
^^^^^^^^^^^^

* boolean

hasMailListWithName
-------------------


Parameters
^^^^^^^^^^

* in AString aName

Return value
^^^^^^^^^^^^

* boolean

addCard
-------

Adds a card to the database.
This card does not need to be of the same type as the database, e.g., one
can add an nsIAbLDAPCard to an nsIAbMDBDirectory.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` card

Return value
^^^^^^^^^^^^

* :doc:`nsIAbCard`

  "Real" card (eg nsIAbLDAPCard) that can be used for some
  extra functions.

modifyCard
----------

Modifies a card in the database to match that supplied.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` modifiedCard

deleteCards
-----------

Deletes the array of cards from the database.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIAbCard`> aCards

  The cards to delete from the database.

dropCard
--------


Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` card
* in boolean needToCopyCard

useForAutocomplete
------------------

Whether or not the directory should be searched when doing autocomplete,
(currently by using GetChildCards); LDAP does not support this in online
mode, so that should return false; additionally any other directory types
that also do not support GetChildCards should return false.

Parameters
^^^^^^^^^^

* in ACString aIdentityKey

Return value
^^^^^^^^^^^^

* boolean

  True if this directory should/can be used during
  local autocomplete.

addMailList
-----------

Creates a new mailing list in the directory. Currently only supported
for top-level directories.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` list

  The new mailing list to add.

Return value
^^^^^^^^^^^^

* :doc:`nsIAbDirectory`

  The mailing list directory added, which may have been modified.

editMailListToDatabase
----------------------

Edits an existing mailing list (specified as listCard) into its parent
directory. You should call this function on the resource with the same
uri as the listCard.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` listCard

  A nsIAbCard version of the mailing list with the new
  values.

copyMailList
------------


Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` srcList

getIntValue
-----------

@name  getXXXValue
Helper functions to get different types of pref, but return a default
value if a pref value was not obtained.
@exception           NS_ERROR_NOT_INITIALIZED if the pref branch couldn't
be obtained (e.g. dirPrefId isn't set).

Parameters
^^^^^^^^^^

* in string aName
* in long aDefaultValue

Return value
^^^^^^^^^^^^

* long

  The value of the pref or the default value.

getBoolValue
------------


Parameters
^^^^^^^^^^

* in string aName
* in boolean aDefaultValue

Return value
^^^^^^^^^^^^

* boolean

getStringValue
--------------


Parameters
^^^^^^^^^^

* in string aName
* in ACString aDefaultValue

Return value
^^^^^^^^^^^^

* ACString

getLocalizedStringValue
-----------------------


Parameters
^^^^^^^^^^

* in string aName
* in AUTF8String aDefaultValue

Return value
^^^^^^^^^^^^

* AUTF8String

setIntValue
-----------

The following attributes are read from an nsIAbDirectory via the above methods:
HidesRecipients (Boolean)
If true, and this nsIAbDirectory is a mailing list, then when sending mail to
this list, recipients addresses will be hidden from one another by sending
via BCC.
@name  setXXXValue
Helper functions to set different types of pref values.
@exception           NS_ERROR_NOT_INITIALIZED if the pref branch couldn't
be obtained (e.g. dirPrefId isn't set).

Parameters
^^^^^^^^^^

* in string aName
* in long aValue

setBoolValue
------------


Parameters
^^^^^^^^^^

* in string aName
* in boolean aValue

setStringValue
--------------


Parameters
^^^^^^^^^^

* in string aName
* in ACString aValue

setLocalizedStringValue
-----------------------


Parameters
^^^^^^^^^^

* in string aName
* in AUTF8String aValue

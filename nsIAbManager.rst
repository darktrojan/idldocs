============
nsIAbManager
============

nsIAbManager is an interface to the main address book manager
via the contract id "@mozilla.org/abmanager;1"

It contains the main functions to create and delete address books as well
as some helper functions.

Constants
=========

LDAP_DIRECTORY_TYPE
-------------------

**Type**: ``unsigned long``

**Value**: ``0``


MAPI_DIRECTORY_TYPE
-------------------

**Type**: ``unsigned long``

**Value**: ``3``


JS_DIRECTORY_TYPE
-----------------

**Type**: ``unsigned long``

**Value**: ``101``


CARDDAV_DIRECTORY_TYPE
----------------------

**Type**: ``unsigned long``

**Value**: ``102``


ASYNC_DIRECTORY_TYPE
--------------------

**Type**: ``unsigned long``

**Value**: ``103``


Methods
=======

getDirectory
------------

Returns the directory that represents the supplied URI.

Parameters
^^^^^^^^^^

* ``in ACString aURI``
  The URI of the address book to find.

Return value
^^^^^^^^^^^^

* ``nsIAbDirectory``
  The found address book.

getDirectoryFromId
------------------

Returns the directory that has the supplied dirPrefId.

Parameters
^^^^^^^^^^

* ``in ACString aDirPrefId``

Return value
^^^^^^^^^^^^

* ``nsIAbDirectory``
  The found AB directory.

getDirectoryFromUID
-------------------

Returns the directory that has the supplied UID.

Parameters
^^^^^^^^^^

* ``in ACString aUID``

Return value
^^^^^^^^^^^^

* ``nsIAbDirectory``
  The found AB directory.

newAddressBook
--------------

Creates a new address book.

Parameters
^^^^^^^^^^

* ``in AString aDirName``
  The description of the address book.
* ``in ACString aURI``
  The URI for the address book. This is specific to each
  type of address book.
* ``in unsigned long aType``
  One of the *_DIRECTORY_TYPE constants.
* ``in ACString aPrefName``
  Overrides the default of ldap_2.servers.<aDirName>
  (note that the caller must ensure its uniqueness).

Return value
^^^^^^^^^^^^

* ``ACString``

addAddressBook
--------------

Adds a previously created address book object. If it has not been removed
(using `deleteAddressBook`) it will be removed at the end of the session.

Parameters
^^^^^^^^^^

* ``in nsIAbDirectory aDir``

Return value
^^^^^^^^^^^^

* ``void``

deleteAddressBook
-----------------

Deletes an address book.

Parameters
^^^^^^^^^^

* ``in ACString aURI``
  The URI for the address book. This is specific to each
  type of address book.

Return value
^^^^^^^^^^^^

* ``void``

mailListNameExists
------------------

Finds out if the mailing list name exists in any address book.

Parameters
^^^^^^^^^^

* ``in AString name``

Return value
^^^^^^^^^^^^

* ``boolean``
  True if the name exists.

directoryNameExists
-------------------

Finds out if the directory name already exists.

Parameters
^^^^^^^^^^

* ``in AString name``

Return value
^^^^^^^^^^^^

* ``boolean``
  True if a directory called name already exists.

cardForEmailAddress
-------------------

Returns an address book card for the specified email address if found, in
any directory. The first matching card found is returned.
*** Results of this function are cached! ***
This function is for where speed is more important than accuracy. Results
are stored in a cache until 60s passes without this function being called.
The address book *could* change in this time, in a way that produces a
different result, but probably won't.
@see    nsIAbCard.cardForEmailAddress

Parameters
^^^^^^^^^^

* ``in AUTF8String emailAddress``
  The email address to find in any of the email address
  fields. If emailAddress is empty, the directories
  won't be searched and the function will return as if
  no card was found.

Return value
^^^^^^^^^^^^

* ``nsIAbCard``
  An nsIAbCard if one was found, else returns NULL.

getMailListFromName
-------------------

Returns the mailing lists that has the supplied name.

Parameters
^^^^^^^^^^

* ``in AString aName``

Return value
^^^^^^^^^^^^

* ``nsIAbDirectory``
  The found AB directory.

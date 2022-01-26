=====================
nsIImportAddressBooks
=====================

`mailnews/import/public/nsIImportAddressBooks.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportAddressBooks.idl>`_


Methods
=======

GetSupportsMultiple
-------------------

``boolean GetSupportsMultiple()``

Does this interface supports 1 or 1..n address books.  You only get to
choose 1 location so for formats where 1..n address books are imported
from a directory, then return true.  For a 1 to 1 relationship between
location and address books return false.

Return value
^^^^^^^^^^^^

* boolean

GetAutoFind
-----------

``boolean GetAutoFind(description)``

If the address book is not found via a file location, then return true
along with a description string of how or where the address book is
located. If it is a file location then return false.
If true, return a string like: "Outlook address book".
If false, GetDefaultLocation will be called.

Parameters
^^^^^^^^^^

* out wstring description

Return value
^^^^^^^^^^^^

* boolean

GetNeedsFieldMap
----------------

``boolean GetNeedsFieldMap(location)``

Returns true if the address book needs the user to specify a field map for
address books imported from this format.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` location

Return value
^^^^^^^^^^^^

* boolean

GetDefaultLocation
------------------

``void GetDefaultLocation(location, found, userVerify)``

If found and userVerify BOTH return false, then it is assumed that this
means an error - address book cannot be found on this machine.
If userVerify is true, the user will have an opportunity to specify a
different location to import address book from.

Parameters
^^^^^^^^^^

* out :doc:`nsIFile` location
* out boolean found
* out boolean userVerify

findAddressBooks
----------------

``Array<nsIImportABDescriptor> findAddressBooks(location)``

Returns an array containing an nsIImportABDescriptor for each
address book.  The array is not sorted before display to the user.
location is null if GetAutoFind returned true.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` location

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIImportABDescriptor`>

InitFieldMap
------------

``void InitFieldMap(fieldMap)``

Fill in defaults (if any) for a field map for importing address books from
this location.

Parameters
^^^^^^^^^^

* in :doc:`nsIImportFieldMap` fieldMap

ImportAddressBook
-----------------

``void ImportAddressBook(aSource, aDestination, aFieldMap, aSupportService, aErrorLog, aSuccessLog, aFatalError)``

Import a specific address book into the destination file supplied.
If an error occurs that is non-fatal, the destination will be deleted and
other address book will be imported.  If a fatal error occurs, the
destination will be deleted and the import operation will abort.

Parameters
^^^^^^^^^^

* in :doc:`nsIImportABDescriptor` aSource
* in :doc:`nsIAbDirectory` aDestination
* in :doc:`nsIImportFieldMap` aFieldMap
* in :doc:`nsISupports` aSupportService
* out wstring aErrorLog
* out wstring aSuccessLog
* out boolean aFatalError

GetImportProgress
-----------------

``unsigned long GetImportProgress()``

Return the amount of the address book that has been imported so far. This
number is used to present progress information and must never be larger
than the size specified in nsIImportABDescriptor.GetSize(); May be called
from a different thread than ImportAddressBook()

Return value
^^^^^^^^^^^^

* unsigned long

SetSampleLocation
-----------------

``void SetSampleLocation(location)``

Set the location for reading sample data, this should be the same as what
is passed later to FindAddressBooks.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` location

GetSampleData
-------------

``wstring GetSampleData(recordNumber, recordExists)``

Return a string of sample data for a record, each field is separated by a
newline (which means no newlines in the fields!)
This is only supported by address books which use field maps and is used
by the field map UI to allow the user to properly align fields to be
imported.

Parameters
^^^^^^^^^^

* in long recordNumber
* out boolean recordExists

Return value
^^^^^^^^^^^^

* wstring

  a string of sample data for the desired record

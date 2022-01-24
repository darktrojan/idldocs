================
nsIAbLDIFService
================


Methods
=======

isLDIFFile
----------

Determine if a file is likely to be an LDIF file based on field
names that commonly appear in LDIF files.

Parameters
^^^^^^^^^^

* ``in nsIFile aSrc``
  The file to examine

Return value
^^^^^^^^^^^^

* ``boolean``
  true if the file appears to be of LDIF type,
  false otherwise

importLDIFFile
--------------

Imports a file into the specified address book.

Parameters
^^^^^^^^^^

* ``in nsIAbDirectory aDirectory``
  The address book to import addresses into.
* ``in nsIFile aSrc``
  The file to import addresses from.
* ``in boolean aStoreLocAsHome``
  Stores the address as a home rather than work
  address.
* ``inout unsigned long aProgress``
  May be null, but if a pointer is supplied,
  then it will be updated regularly with the
  current position of reading from the file.

Return value
^^^^^^^^^^^^

* ``void``

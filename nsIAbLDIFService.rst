================
nsIAbLDIFService
================


Methods
=======

isLDIFFile
----------

Determine if a file is likely to be an LDIF file based on field
names that commonly appear in LDIF files.

@param       aSrc   The file to examine

@return      true if the file appears to be of LDIF type,
false otherwise

Parameters
^^^^^^^^^^

* ``in nsIFile aSrc``

Return value
^^^^^^^^^^^^

* ``boolean``

importLDIFFile
--------------

Imports a file into the specified address book.

@param       aDirectory      The address book to import addresses into.

@param       aSrc            The file to import addresses from.

@param       aStoreLocAsHome Stores the address as a home rather than work
address.

@param       aProgress       May be null, but if a pointer is supplied,
then it will be updated regularly with the
current position of reading from the file.


Parameters
^^^^^^^^^^

* ``in nsIAbDirectory aDirectory``
* ``in nsIFile aSrc``
* ``in boolean aStoreLocAsHome``
* ``inout unsigned long aProgress``

Return value
^^^^^^^^^^^^

* ``void``

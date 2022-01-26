=====================
nsIImportABDescriptor
=====================

`mailnews/import/public/nsIImportABDescriptor.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportABDescriptor.idl>`_

Implementation Note:

The default implementation can be obtained from
nsIImportService::CreateNewABDescriptor();

You should only be interested in using this class if you implement
the nsIImportAddressBooks interface in which case, just using the service to
create new ones should work fine for you.  If not, implement your
own.

Properties
==========

identifier
----------

``attribute unsigned long identifier``

use the following 2 attributes however you'd like to
refer to a specific address book

ref
---

``attribute unsigned long ref``

size
----

``attribute unsigned long size``

Doesn't have to be accurate, this is merely used to report progress.
If you're importing a file, using file size and reporting progress
as the number of bytes processed so far makes sense.  For other formats
returning the number of records may make more sense.

preferredName
-------------

``attribute AString preferredName``

The preferred name for this address book.  Depending upon how the
user selected import, the caller of the nsIImportAddressBooks interface
may use this name to create the destination address book or it may
ignore it.  However, this must be provided in all cases as it is
also displayed in the UI to the user.

abFile
------

``attribute nsIFile abFile``

For address books that want a file descriptor to locate the address book.
For formats that do not, use identifier & ref to refer to the address book
OR implement your own nsIImportABDescriptor that contains additional data
necessary to identify specific address books,

import
------

``attribute boolean import``

Set by the UI to indicate whether or not this address book should be imported.

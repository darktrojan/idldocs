=============
nsIImportMail
=============

`mailnews/import/public/nsIImportMail.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportMail.idl>`_


Methods
=======

GetDefaultLocation
------------------

``void GetDefaultLocation(location, found, userVerify)``

Parameters
^^^^^^^^^^

* out :doc:`nsIFile` location
* out boolean found
* out boolean userVerify

findMailboxes
-------------

``Array<nsIImportMailboxDescriptor> findMailboxes(location)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` location

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIImportMailboxDescriptor`>

ImportMailbox
-------------

``void ImportMailbox(source, dstFolder, errorLog, successLog, fatalError)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImportMailboxDescriptor` source
* in :doc:`nsIMsgFolder` dstFolder
* out wstring errorLog
* out wstring successLog
* out boolean fatalError

GetImportProgress
-----------------

``unsigned long GetImportProgress()``

Return value
^^^^^^^^^^^^

* unsigned long

translateFolderName
-------------------

``AString translateFolderName(aFolderName)``

Parameters
^^^^^^^^^^

* in AString aFolderName

Return value
^^^^^^^^^^^^

* AString

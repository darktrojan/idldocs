================
nsIImportService
================

`mailnews/import/public/nsIImportService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportService.idl>`_


Methods
=======

DiscoverModules
---------------

``void DiscoverModules()``

GetModuleCount
--------------

``long GetModuleCount(filter)``

Parameters
^^^^^^^^^^

* in string filter

Return value
^^^^^^^^^^^^

* long

GetModuleInfo
-------------

``void GetModuleInfo(filter, index, name, description)``

Parameters
^^^^^^^^^^

* in string filter
* in long index
* out AString name
* out AString description

GetModuleName
-------------

``AString GetModuleName(filter, index)``

Parameters
^^^^^^^^^^

* in string filter
* in long index

Return value
^^^^^^^^^^^^

* AString

GetModuleDescription
--------------------

``AString GetModuleDescription(filter, index)``

Parameters
^^^^^^^^^^

* in string filter
* in long index

Return value
^^^^^^^^^^^^

* AString

GetModule
---------

``nsIImportModule GetModule(filter, index)``

Parameters
^^^^^^^^^^

* in string filter
* in long index

Return value
^^^^^^^^^^^^

* :doc:`nsIImportModule`

CreateNewFieldMap
-----------------

``nsIImportFieldMap CreateNewFieldMap()``

Return value
^^^^^^^^^^^^

* :doc:`nsIImportFieldMap`

CreateNewMailboxDescriptor
--------------------------

``nsIImportMailboxDescriptor CreateNewMailboxDescriptor()``

Return value
^^^^^^^^^^^^

* :doc:`nsIImportMailboxDescriptor`

CreateNewABDescriptor
---------------------

``nsIImportABDescriptor CreateNewABDescriptor()``

Return value
^^^^^^^^^^^^

* :doc:`nsIImportABDescriptor`

CreateNewGenericMail
--------------------

``nsIImportGeneric CreateNewGenericMail()``

Return value
^^^^^^^^^^^^

* :doc:`nsIImportGeneric`

CreateNewGenericAddressBooks
----------------------------

``nsIImportGeneric CreateNewGenericAddressBooks()``

Return value
^^^^^^^^^^^^

* :doc:`nsIImportGeneric`

CreateRFC822Message
-------------------

``void CreateRFC822Message(aIdentity, aMsgFields, aBodytype, aBody, aCreateAsDraft, aLoadedAttachments, aEmbeddedObjects, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aIdentity
* in :doc:`nsIMsgCompFields` aMsgFields
* in string aBodytype
* in ACString aBody
* in boolean aCreateAsDraft
* in Array<:doc:`nsIMsgAttachedFile`> aLoadedAttachments
* in Array<:doc:`nsIMsgEmbeddedImageData`> aEmbeddedObjects
* in :doc:`nsIMsgSendListener` aListener

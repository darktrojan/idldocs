===============
nsIImportModule
===============

`mailnews/import/public/nsIImportModule.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportModule.idl>`_


Properties
==========

name
----

``readonly attribute wstring name``

description
-----------

``readonly attribute wstring description``

supports
--------

``readonly attribute string supports``

supportsUpgrade
---------------

``readonly attribute boolean supportsUpgrade``

Methods
=======

GetImportInterface
------------------

``nsISupports GetImportInterface(importType)``

Parameters
^^^^^^^^^^

* in string importType

Return value
^^^^^^^^^^^^

* :doc:`nsISupports`

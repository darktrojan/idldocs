==========================
nsIImportMailboxDescriptor
==========================

`mailnews/import/public/nsIImportMailboxDescriptor.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportMailboxDescriptor.idl>`_


Properties
==========

identifier
----------

``attribute unsigned long identifier``

depth
-----

``attribute unsigned long depth``

size
----

``attribute unsigned long size``

import
------

``attribute boolean import``

file
----

``readonly attribute nsIFile file``

Methods
=======

GetDisplayName
--------------

``wstring GetDisplayName()``

Return value
^^^^^^^^^^^^

* wstring

SetDisplayName
--------------

``void SetDisplayName(name)``

Parameters
^^^^^^^^^^

* in wstring name

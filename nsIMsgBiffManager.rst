=================
nsIMsgBiffManager
=================

`mailnews/base/public/nsIMsgBiffManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgBiffManager.idl>`_


Methods
=======

init
----

``void init()``

addServerBiff
-------------

``void addServerBiff(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

removeServerBiff
----------------

``void removeServerBiff(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

forceBiff
---------

``void forceBiff(server)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

forceBiffAll
------------

``void forceBiffAll()``

shutdown
--------

``void shutdown()``

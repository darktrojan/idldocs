=========================
nsIIncomingServerListener
=========================

`mailnews/base/public/nsIIncomingServerListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIIncomingServerListener.idl>`_


Methods
=======

onServerLoaded
--------------

``void onServerLoaded(server)``

Notification sent when a server is first loaded into the account manager.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

onServerUnloaded
----------------

``void onServerUnloaded(server)``

Notification sent when a server is unloaded from the account manager.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

onServerChanged
---------------

``void onServerChanged(server)``

Notification sent when a server hostname or username changes.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` server

===================
nsINoIncomingServer
===================

`mailnews/local/public/nsINoIncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsINoIncomingServer.idl>`_


Methods
=======

copyDefaultMessages
-------------------

``void copyDefaultMessages(folderNameOnDisk)``

Copy the default messages (e.g. Templates) from
bin/defaults/messenger/<folderNameOnDisk> to <rootFolder>/<folderNameOnDisk>.
This is useful when first creating the standard folders (like Templates).

Parameters
^^^^^^^^^^

* in string folderNameOnDisk

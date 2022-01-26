==========================
nsIMsgDBViewCommandUpdater
==========================

`mailnews/base/public/nsIMsgDBView.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgDBView.idl>`_


Methods
=======

updateCommandStatus
-------------------

``void updateCommandStatus()``

displayMessageChanged
---------------------

``void displayMessageChanged(aFolder, aSubject, aKeywords)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in AString aSubject
* in ACString aKeywords

updateNextMessageAfterDelete
----------------------------

``void updateNextMessageAfterDelete()``

allows the backend to tell the front end to re-determine
which message we should selet after a delete or move

summarizeSelection
------------------

``boolean summarizeSelection()``

tell the front end that the selection has changed, and may need to be
resummarized.

Return value
^^^^^^^^^^^^

* boolean

  true if we did summarize, false otherwise.

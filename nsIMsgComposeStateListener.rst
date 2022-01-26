==========================
nsIMsgComposeStateListener
==========================

`mailnews/compose/public/nsIMsgCompose.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgCompose.idl>`_


Methods
=======

NotifyComposeFieldsReady
------------------------

``void NotifyComposeFieldsReady()``

ComposeProcessDone
------------------

``void ComposeProcessDone(aResult)``

Parameters
^^^^^^^^^^

* in nsresult aResult

SaveInFolderDone
----------------

``void SaveInFolderDone(folderName)``

Parameters
^^^^^^^^^^

* in string folderName

NotifyComposeBodyReady
----------------------

``void NotifyComposeBodyReady()``

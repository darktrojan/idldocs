====================
nsIMsgStatusFeedback
====================

`mailnews/base/public/nsIMsgStatusFeedback.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgStatusFeedback.idl>`_


Methods
=======

showStatusString
----------------

``void showStatusString(aStatus)``

Parameters
^^^^^^^^^^

* in AString aStatus

startMeteors
------------

``void startMeteors()``

stopMeteors
-----------

``void stopMeteors()``

showProgress
------------

``void showProgress(aPercent)``

Parameters
^^^^^^^^^^

* in long aPercent

setStatusString
---------------

``void setStatusString(aStatus)``

Parameters
^^^^^^^^^^

* in AString aStatus

setWrappedStatusFeedback
------------------------

``void setWrappedStatusFeedback(aStatusFeedback)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgStatusFeedback` aStatusFeedback

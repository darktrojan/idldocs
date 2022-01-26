================
nsIMsgSendReport
================

`mailnews/compose/public/nsIMsgSendReport.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSendReport.idl>`_


Constants
=========

process_Current
---------------

**Type**: ``long``

**Value**: ``-1``


process_BuildMessage
--------------------

**Type**: ``long``

**Value**: ``0``


process_NNTP
------------

**Type**: ``long``

**Value**: ``1``


process_SMTP
------------

**Type**: ``long``

**Value**: ``2``


process_Copy
------------

**Type**: ``long``

**Value**: ``3``


process_Filter
--------------

**Type**: ``long``

**Value**: ``4``


process_FCC
-----------

**Type**: ``long``

**Value**: ``5``


Properties
==========

deliveryMode
------------

``attribute long deliveryMode``

currentProcess
--------------

``attribute long currentProcess``

Methods
=======

reset
-----

``void reset()``

setProceeded
------------

``void setProceeded(process, proceeded)``

Parameters
^^^^^^^^^^

* in long process
* in boolean proceeded

setError
--------

``void setError(process, error, overwriteError)``

Parameters
^^^^^^^^^^

* in long process
* in nsresult error
* in boolean overwriteError

setMessage
----------

``void setMessage(process, message, overwriteMessage)``

Parameters
^^^^^^^^^^

* in long process
* in wstring message
* in boolean overwriteMessage

getProcessReport
----------------

``nsIMsgProcessReport getProcessReport(process)``

Parameters
^^^^^^^^^^

* in long process

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgProcessReport`

displayReport
-------------

``nsresult displayReport(prompt, showErrorOnly, dontShowReportTwice)``

Parameters
^^^^^^^^^^

* in :doc:`nsIPrompt` prompt
* in boolean showErrorOnly
* in boolean dontShowReportTwice

Return value
^^^^^^^^^^^^

* nsresult

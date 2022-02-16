====================
nsINNTPNewsgroupList
====================

`mailnews/news/public/nsINNTPNewsgroupList.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINNTPNewsgroupList.idl>`_

A utility class for nsINNTPProtocol that handles the list of new headers.

Properties
==========

getOldMessages
--------------

``attribute boolean getOldMessages``

Methods
=======

initialize
----------

``void initialize(runningURL, newsFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsINntpUrl` runningURL
* in :doc:`nsIMsgNewsFolder` newsFolder

getRangeOfArtsToDownload
------------------------

``long getRangeOfArtsToDownload(aMsgWindow, first_message, last_message, maxextra, real_first_message, real_last_message)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in long first_message
* in long last_message
* in long maxextra
* out long real_first_message
* out long real_last_message

Return value
^^^^^^^^^^^^

* long

addToKnownArticles
------------------

``void addToKnownArticles(first_message, last_message)``

Parameters
^^^^^^^^^^

* in long first_message
* in long last_message

initXOVER
---------

``void initXOVER(first_message, last_message)``

Initializes the internal state to get the messages.

This method should be called before sending the line
<tt>XOVER @arg first_message-@arg last_message</tt> to the server.

Parameters
^^^^^^^^^^

* in long first_message
* in long last_message

processXOVERLINE
----------------

``void processXOVERLINE(line, status)``

Parameters
^^^^^^^^^^

* in string line
* out unsigned long status

resetXOVER
----------

``void resetXOVER()``

finishXOVERLINE
---------------

``void finishXOVERLINE(status, newstatus)``

Parameters
^^^^^^^^^^

* in long status
* out long newstatus

initXHDR
--------

``ACString initXHDR()``

Initializes the state in preparation for a call to XHDR.

Return value
^^^^^^^^^^^^

* ACString

  The next header to get, or an empty string if done.

processXHDRLine
---------------

``void processXHDRLine(aLine)``

Processes a line of the server's response to XHDR.

It will calculate the message number and other information itself, so the
unadulterated line itself should be sent.

Parameters
^^^^^^^^^^

* in ACString aLine

initHEAD
--------

``void initHEAD(aMessage)``

Initializes the internal state to process a HEAD command.

This method should be called before sending the line
<tt>HEAD @arg aMessage</tt> to the server.

Parameters
^^^^^^^^^^

* in long aMessage

processHEADLine
---------------

``void processHEADLine(aLine)``

Processes a line of the server's response to HEAD.

This will not check for a quoted '.' at the beginning.

Parameters
^^^^^^^^^^

* in ACString aLine

HEADFailed
----------

``void HEADFailed(aMessage)``

Manages the internal state if the call to HEAD failed.

Parameters
^^^^^^^^^^

* in long aMessage

callFilters
-----------

``void callFilters()``

Calls the filters after all messages have been processed.

This method also cleans out some internal state relating to the messages
that have been processed, so it should always be called at the end of
XOVER/XHDR/HEAD processing.

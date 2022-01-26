=====================
nsIPop3IncomingServer
=====================

`mailnews/local/public/nsIPop3IncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIPop3IncomingServer.idl>`_


Properties
==========

leaveMessagesOnServer
---------------------

``attribute boolean leaveMessagesOnServer``

headersOnly
-----------

``attribute boolean headersOnly``

deleteMailLeftOnServer
----------------------

``attribute boolean deleteMailLeftOnServer``

dotFix
------

``attribute boolean dotFix``

pop3CapabilityFlags
-------------------

``attribute unsigned long pop3CapabilityFlags``

deleteByAgeFromServer
---------------------

``attribute boolean deleteByAgeFromServer``

numDaysToLeaveOnServer
----------------------

``attribute long numDaysToLeaveOnServer``

runningProtocol
---------------

``attribute nsIPop3Protocol runningProtocol``

authenticated
-------------

``attribute boolean authenticated``

deferredToAccount
-----------------

``attribute ACString deferredToAccount``

deferGetNewMail
---------------

``attribute boolean deferGetNewMail``

Methods
=======

addUidlToMark
-------------

``void addUidlToMark(aUidl, newStatus)``

Parameters
^^^^^^^^^^

* in string aUidl
* in int32_t newStatus

markMessages
------------

``void markMessages()``

downloadMailFromServers
-----------------------

``void downloadMailFromServers(aServers, aMsgWindow, aFolder, aListener)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIPop3IncomingServer`> aServers
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIUrlListener` aListener

========================
nsIMsgFilterCustomAction
========================

`mailnews/search/public/nsIMsgFilterCustomAction.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterCustomAction.idl>`_

describes a custom action added to a message filter

Properties
==========

id
--

``readonly attribute ACString id``

name
----

``readonly attribute AString name``

allowDuplicates
---------------

``attribute boolean allowDuplicates``

isAsync
-------

``readonly attribute boolean isAsync``

needsBody
---------

``readonly attribute boolean needsBody``

Methods
=======

isValidForType
--------------

``boolean isValidForType(type, scope)``

Is this custom action valid for a particular filter type?

Parameters
^^^^^^^^^^

* in nsMsgFilterTypeType type
* in nsMsgSearchScopeValue scope

Return value
^^^^^^^^^^^^

* boolean

  true if valid

validateActionValue
-------------------

``AUTF8String validateActionValue(actionValue, actionFolder, filterType)``

After the user inputs a particular action value for the action, determine
if that value is valid.

Parameters
^^^^^^^^^^

* in AUTF8String actionValue
* in :doc:`nsIMsgFolder` actionFolder
* in nsMsgFilterTypeType filterType

Return value
^^^^^^^^^^^^

* AUTF8String

  errorMessage        A localized message to display if invalid
  Set to null if the actionValue is valid

applyAction
-----------

``void applyAction(msgHdrs, actionValue, copyListener, filterType, msgWindow)``

Apply the custom action to an array of messages

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> msgHdrs
* in AUTF8String actionValue
* in :doc:`nsIMsgCopyServiceListener` copyListener
* in nsMsgFilterTypeType filterType
* in :doc:`nsIMsgWindow` msgWindow

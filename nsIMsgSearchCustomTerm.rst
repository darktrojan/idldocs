======================
nsIMsgSearchCustomTerm
======================

`mailnews/search/public/nsIMsgSearchCustomTerm.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchCustomTerm.idl>`_

describes a custom term added to a message search or filter

Properties
==========

id
--

``readonly attribute ACString id``

globally unique string to identify this search term.
recommended form: ExtensionName@example.com#TermName
Commas and quotes are not allowed, the id must not
parse to an integer, and names of standard search
attributes in SearchAttribEntryTable in nsMsgSearchTerm.cpp
are not allowed.

name
----

``readonly attribute AString name``

needsBody
---------

``readonly attribute boolean needsBody``

Methods
=======

getEnabled
----------

``boolean getEnabled(scope, op)``

Is this custom term enabled?

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope
* in nsMsgSearchOpValue op

Return value
^^^^^^^^^^^^

* boolean

  true if enabled

getAvailable
------------

``boolean getAvailable(scope, op)``

Is this custom term available?

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope
* in nsMsgSearchOpValue op

Return value
^^^^^^^^^^^^

* boolean

  true if available

getAvailableOperators
---------------------

``Array<nsMsgSearchOpValue> getAvailableOperators(scope)``

List the valid operators for this term.

Parameters
^^^^^^^^^^

* in nsMsgSearchScopeValue scope

Return value
^^^^^^^^^^^^

* Array<nsMsgSearchOpValue>

  array of operators

match
-----

``boolean match(msgHdr, searchValue, searchOp)``

Apply the custom search term to a message

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in AUTF8String searchValue
* in nsMsgSearchOpValue searchOp

Return value
^^^^^^^^^^^^

* boolean

  true if the term matches the message, else false

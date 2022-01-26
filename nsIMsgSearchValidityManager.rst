===========================
nsIMsgSearchValidityManager
===========================

`mailnews/search/public/nsIMsgSearchValidityManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchValidityManager.idl>`_


Methods
=======

getTable
--------

``nsIMsgSearchValidityTable getTable(scope)``

Parameters
^^^^^^^^^^

* in nsMsgSearchValidityScope scope

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgSearchValidityTable`

getAttributeProperty
--------------------

``AString getAttributeProperty(aSearchAttribute)``

Given a search attribute (which is an internal numerical id), return
the string name that you can use as a key to look up the localized
string in the search-attributes.properties file.

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue aSearchAttribute

Return value
^^^^^^^^^^^^

* AString

  localization-friendly string representation
  of the attribute

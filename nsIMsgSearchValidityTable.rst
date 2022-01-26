=========================
nsIMsgSearchValidityTable
=========================

`mailnews/search/public/nsIMsgSearchValidityTable.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgSearchValidityTable.idl>`_


Properties
==========

numAvailAttribs
---------------

``readonly attribute long numAvailAttribs``

Methods
=======

setAvailable
------------

``void setAvailable(attrib, op, active)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op
* in boolean active

setEnabled
----------

``void setEnabled(attrib, op, enabled)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op
* in boolean enabled

setValidButNotShown
-------------------

``void setValidButNotShown(attrib, op, valid)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op
* in boolean valid

getAvailable
------------

``boolean getAvailable(attrib, op)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op

Return value
^^^^^^^^^^^^

* boolean

getEnabled
----------

``boolean getEnabled(attrib, op)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op

Return value
^^^^^^^^^^^^

* boolean

getValidButNotShown
-------------------

``boolean getValidButNotShown(attrib, op)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib
* in nsMsgSearchOpValue op

Return value
^^^^^^^^^^^^

* boolean

getAvailableAttributes
----------------------

``Array<nsMsgSearchAttribValue> getAvailableAttributes()``

Return value
^^^^^^^^^^^^

* Array<nsMsgSearchAttribValue>

getAvailableOperators
---------------------

``Array<nsMsgSearchOpValue> getAvailableOperators(attrib)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue attrib

Return value
^^^^^^^^^^^^

* Array<nsMsgSearchOpValue>

setDefaultAttrib
----------------

``void setDefaultAttrib(defaultAttrib)``

Parameters
^^^^^^^^^^

* in nsMsgSearchAttribValue defaultAttrib

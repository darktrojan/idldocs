===================
nsILDAPModification
===================

`mailnews/addrbook/public/nsILDAPModification.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPModification.idl>`_


Constants
=========

MOD_ADD
-------

**Type**: ``long``

**Value**: ``0``

Add operation

MOD_DELETE
----------

**Type**: ``long``

**Value**: ``1``

Delete operation

MOD_REPLACE
-----------

**Type**: ``long``

**Value**: ``2``

Replace operation

MOD_BVALUES
-----------

**Type**: ``long``

**Value**: ``128``

Values are BER encoded

Properties
==========

operation
---------

``attribute long operation``

The operation to perform.

type
----

``attribute ACString type``

The attribute to modify.

values
------

``attribute Array<nsILDAPBERValue> values``

The array of values this modification sets for the attribute

Methods
=======

setUpModification
-----------------

``void setUpModification(aOperation, aType, aValues)``

Function that allows all the attributes to be set at the same
time to avoid multiple function calls.

Parameters
^^^^^^^^^^

* in long aOperation
* in ACString aType
* in Array<:doc:`nsILDAPBERValue`> aValues

setUpModificationOneValue
-------------------------

``void setUpModificationOneValue(aOperation, aType, aValue)``

Parameters
^^^^^^^^^^

* in long aOperation
* in ACString aType
* in :doc:`nsILDAPBERValue` aValue

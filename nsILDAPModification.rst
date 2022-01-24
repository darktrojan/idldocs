===================
nsILDAPModification
===================


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

Methods
=======

setUpModification
-----------------

Function that allows all the attributes to be set at the same
time to avoid multiple function calls.

Parameters
^^^^^^^^^^

* in long aOperation
* in ACString aType
* in Array<:doc:`nsILDAPBERValue`> aValues

setUpModificationOneValue
-------------------------


Parameters
^^^^^^^^^^

* in long aOperation
* in ACString aType
* in :doc:`nsILDAPBERValue` aValue

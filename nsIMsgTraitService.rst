==================
nsIMsgTraitService
==================

`mailnews/search/public/nsIMsgTraitService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgTraitService.idl>`_


Properties
==========

lastIndex
---------

``readonly attribute long lastIndex``

the highest ever index for a registered trait. The first trait is 1,
== 0 means no traits are defined

Methods
=======

registerTrait
-------------

``unsigned long registerTrait(id)``

Register a trait. May be called multiple times, but subsequent
calls do not register the trait

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* unsigned long

  the internal index for the registered trait if newly
  registered, else 0

unRegisterTrait
---------------

``void unRegisterTrait(id)``

Unregister a trait.

Parameters
^^^^^^^^^^

* in ACString id

isRegistered
------------

``boolean isRegistered(id)``

is a trait registered?

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* boolean

  true if registered

setName
-------

``void setName(id, name)``

set the trait name, which is an optional short description of the trait

Parameters
^^^^^^^^^^

* in ACString id
* in ACString name

getName
-------

``ACString getName(id)``

get the trait name, which is an optional short description of the trait

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* ACString

  description of the trait

getIndex
--------

``unsigned long getIndex(id)``

get the internal index number for the trait.

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* unsigned long

  internal index number for the trait

getId
-----

``ACString getId(index)``

get the trait universal identifier for an internal trait index

Parameters
^^^^^^^^^^

* in unsigned long index

Return value
^^^^^^^^^^^^

* ACString

  trait universal identifier

setEnabled
----------

``void setEnabled(id, enabled)``

enable the trait for analysis. Each enabled trait will be analyzed by
the bayesian code. The enabled trait is the "pro" trait that represents
messages matching the trait. Each enabled trait also needs a corresponding
anti trait defined, which represents messages that do not match the trait.
The anti trait does not need to be enabled

Parameters
^^^^^^^^^^

* in ACString id
* in boolean enabled

getEnabled
----------

``boolean getEnabled(id)``

Should this trait be processed by the bayes analyzer?

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* boolean

  true if this is a "pro" trait to process

setAntiId
---------

``void setAntiId(id, antiId)``

set the anti trait, which indicates messages that have been marked as
NOT matching a particular trait.

Parameters
^^^^^^^^^^

* in ACString id
* in ACString antiId

getAntiId
---------

``ACString getAntiId(id)``

get the id of traits that do not match a particular trait

Parameters
^^^^^^^^^^

* in ACString id

Return value
^^^^^^^^^^^^

* ACString

  universal trait identifier for an "anti" trait that does not
  match the "pro" trait messages

getEnabledProIndices
--------------------

``Array<unsigned long> getEnabledProIndices()``

Get an array of "pro" traits to be analyzed by the bayesian code. This is
a "pro" trait of messages that match the trait.
Only enabled traits are returned.
This should return the same number of indices as the corresponding call to
getEnabledAntiIndices().

Return value
^^^^^^^^^^^^

* Array<unsigned long>

  an array of trait internal indices for "pro" trait to analyze

getEnabledAntiIndices
---------------------

``Array<unsigned long> getEnabledAntiIndices()``

Get an array of "anti" traits to be analyzed by the bayesian code. This is
a "anti" trait of messages that do not match the trait.
Only enabled traits are returned.
This should return the same number of indices as the corresponding call to
getEnabledProIndices().

Return value
^^^^^^^^^^^^

* Array<unsigned long>

  an array of trait internal indices for "anti" trait to analyze

addAlias
--------

``void addAlias(aTraitIndex, aTraitAlias)``

Add a trait as an alias of another trait. An alias is a trait whose
counts will be combined with the aliased trait. This allows multiple sets
of corpus data to be used to provide information on a single message
characteristic, while allowing each individual set of corpus data to
retain its own identity.

Parameters
^^^^^^^^^^

* in unsigned long aTraitIndex
* in unsigned long aTraitAlias

removeAlias
-----------

``void removeAlias(aTraitIndex, aTraitAlias)``

Removes a trait as an alias of another trait.

Parameters
^^^^^^^^^^

* in unsigned long aTraitIndex
* in unsigned long aTraitAlias

getAliases
----------

``Array<unsigned long> getAliases(aTraitIndex)``

Get an array of trait aliases for a trait index, if any

Parameters
^^^^^^^^^^

* in unsigned long aTraitIndex

Return value
^^^^^^^^^^^^

* Array<unsigned long>

  an array of internal identifiers for aliases

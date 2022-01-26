================
nsIMsgTagService
================

`mailnews/base/public/nsIMsgTagService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgTagService.idl>`_


Methods
=======

addTag
------

``void addTag(tag, color, ordinal)``

Parameters
^^^^^^^^^^

* in AString tag
* in ACString color
* in ACString ordinal

addTagForKey
------------

``void addTagForKey(key, tag, color, ordinal)``

Parameters
^^^^^^^^^^

* in ACString key
* in AString tag
* in ACString color
* in ACString ordinal

getKeyForTag
------------

``ACString getKeyForTag(tag)``

Parameters
^^^^^^^^^^

* in AString tag

Return value
^^^^^^^^^^^^

* ACString

getTopKey
---------

``ACString getTopKey(keyList)``

Parameters
^^^^^^^^^^

* in ACString keyList

Return value
^^^^^^^^^^^^

* ACString

getTagForKey
------------

``AString getTagForKey(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* AString

setTagForKey
------------

``void setTagForKey(key, tag)``

Parameters
^^^^^^^^^^

* in ACString key
* in AString tag

getColorForKey
--------------

``ACString getColorForKey(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* ACString

getSelectorForKey
-----------------

``AString getSelectorForKey(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* AString

setColorForKey
--------------

``void setColorForKey(key, color)``

Parameters
^^^^^^^^^^

* in ACString key
* in ACString color

getOrdinalForKey
----------------

``ACString getOrdinalForKey(key)``

Parameters
^^^^^^^^^^

* in ACString key

Return value
^^^^^^^^^^^^

* ACString

setOrdinalForKey
----------------

``void setOrdinalForKey(key, ordinal)``

Parameters
^^^^^^^^^^

* in ACString key
* in ACString ordinal

deleteKey
---------

``void deleteKey(key)``

Parameters
^^^^^^^^^^

* in ACString key

getAllTags
----------

``Array<nsIMsgTag> getAllTags()``

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgTag`>

isValidKey
----------

``boolean isValidKey(aKey)``

Parameters
^^^^^^^^^^

* in ACString aKey

Return value
^^^^^^^^^^^^

* boolean

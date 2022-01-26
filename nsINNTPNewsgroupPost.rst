====================
nsINNTPNewsgroupPost
====================

`mailnews/news/public/nsINNTPNewsgroupPost.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINNTPNewsgroupPost.idl>`_


Properties
==========

relayVersion
------------

``attribute string relayVersion``

postingVersion
--------------

``attribute string postingVersion``

from
----

``attribute string from``

date
----

``attribute string date``

newsgroups
----------

``readonly attribute string newsgroups``

subject
-------

``attribute string subject``

path
----

``attribute string path``

replyTo
-------

``attribute string replyTo``

sender
------

``attribute string sender``

followupTo
----------

``attribute string followupTo``

dateReceived
------------

``attribute string dateReceived``

expires
-------

``attribute string expires``

references
----------

``readonly attribute string references``

control
-------

``attribute string control``

distribution
------------

``attribute string distribution``

organization
------------

``attribute string organization``

body
----

``attribute string body``

isControl
---------

``readonly attribute boolean isControl``

postMessageFile
---------------

``attribute nsIFile postMessageFile``

Methods
=======

AddNewsgroup
------------

``void AddNewsgroup(newsgroupName)``

Parameters
^^^^^^^^^^

* in string newsgroupName

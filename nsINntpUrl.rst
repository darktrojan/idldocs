==========
nsINntpUrl
==========

`mailnews/news/public/nsINntpUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINntpUrl.idl>`_

Represents specific attributes to a URL for news usage.

Note that the urls represented by this interface can be one of five schemes:
[s]news, nntp[s], or news-message. Any URI that is valid under RFC 5538 will
be accepted. However, it is possible for some queries to be invalid. There
are also a few important things to note:

- Missing authorities in [s]news: URIs cause nsIMsgMailNewsUrl::server and
nsIMsgMessageUrl::folder to be null.
- nsIMsgMailNewsUrl::server and nsIMsgMessageUrl::folder will be null if the
specified server does not actually exist. In addition, the folder is null
if the group is not currently subscribed on that server.
- Although news-message URIs are parsable, there is no protocol handler
associated with this url. To run these, you should convert these to the
corresponding [s]news or nntp URL, and set the original one in
nsIMsgMessageUrl::uri and ::originalSpec.
- A URI that results in an ActionUnknown will not be run.
- Cancel URIs require the original spec to also be set, so it can find both
the message ID and the group/key combination.
* Some actions require either a group or a message id. Since actions can be
set after the fact, these conditions are not verified.

Constants
=========

ActionUnknown
-------------

**Type**: ``nsNewsAction``

**Value**: ``0``


ActionFetchArticle
------------------

**Type**: ``nsNewsAction``

**Value**: ``1``


ActionFetchPart
---------------

**Type**: ``nsNewsAction``

**Value**: ``2``


ActionSaveMessageToDisk
-----------------------

**Type**: ``nsNewsAction``

**Value**: ``3``


ActionCancelArticle
-------------------

**Type**: ``nsNewsAction``

**Value**: ``4``


ActionPostArticle
-----------------

**Type**: ``nsNewsAction``

**Value**: ``5``


ActionListIds
-------------

**Type**: ``nsNewsAction``

**Value**: ``6``


ActionSearch
------------

**Type**: ``nsNewsAction``

**Value**: ``7``


ActionGetNewNews
----------------

**Type**: ``nsNewsAction``

**Value**: ``8``


ActionListGroups
----------------

**Type**: ``nsNewsAction``

**Value**: ``9``


ActionListNewGroups
-------------------

**Type**: ``nsNewsAction``

**Value**: ``10``


DEFAULT_NNTP_PORT
-----------------

**Type**: ``int32_t``

**Value**: ``119``


DEFAULT_NNTPS_PORT
------------------

**Type**: ``int32_t``

**Value**: ``563``


Properties
==========

messageToPost
-------------

``attribute nsINNTPNewsgroupPost messageToPost``

newsAction
----------

``attribute nsNewsAction newsAction``

The action that this URL will take when run.

Most actions can be automatically determined from the URL spec as follows:

1. The query string is searched for the appropriate action.

2. A non-empty message ID or key is found (sets ActionFetchArticle).

3. A non-empty group is found (ActionGetNewNews or ActionListGroups).

getOldMessages
--------------

``attribute boolean getOldMessages``

group
-----

``readonly attribute ACString group``

The group portion of the URI, if one is present.

This group name is fully unescaped; if you need to construct news URLs with
this value, be sure to escape it first.

messageID
---------

``readonly attribute ACString messageID``

key
---

``readonly attribute nsMsgKey key``

charset
-------

``readonly attribute ACString charset``

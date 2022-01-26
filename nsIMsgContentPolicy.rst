===================
nsIMsgContentPolicy
===================

`mailnews/base/public/nsIMsgContentPolicy.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgContentPolicy.idl>`_

This interface provide functions which help extension developers
add their customized schema to the exposed protocls of nsMsgContentPolicy.
By default, a list of existing protocols (such as imap and nntp)
are allowed to process urls locally, while non-matching urls are required
to be processed as external.
This interface allows additional protocols to be added to
the list of protocols that are processed locally.
Typically this would be used in cases where a new messaging protocol
is being added by an extension.

Methods
=======

addExposedProtocol
------------------

``void addExposedProtocol(aScheme)``

Add the specific aScheme to nsMsgContentPolicy's exposed protocols.

Parameters
^^^^^^^^^^

* in ACString aScheme

removeExposedProtocol
---------------------

``void removeExposedProtocol(aScheme)``

Remove the specific aScheme from nsMsgContentPolicy's exposed protocols.

Parameters
^^^^^^^^^^

* in ACString aScheme

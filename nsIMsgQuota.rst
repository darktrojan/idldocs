===========
nsIMsgQuota
===========

`mailnews/imap/public/nsIMsgImapMailFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIMsgImapMailFolder.idl>`_

nsIMsgQuota defines the quota for a resource within a quota root.
@see RFC 2087

Properties
==========

name
----

``attribute ACString name``

If quota root name not empty, the concatenation of the quota root name
and the resource name separated by a slash , e.g.,
"User Quota / MESSAGE" or with empty quota root name, just resource
name, e.g., "STORAGE".

usage
-----

``attribute unsigned long long usage``

Amount of resource in use for this quota root. E.g., number of messages
or storage in KB (1024 octets).

limit
-----

``attribute unsigned long long limit``

Maximum amount of usage permitted by the server for this quota root
resource.

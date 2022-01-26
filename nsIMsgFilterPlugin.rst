==================
nsIMsgFilterPlugin
==================

`mailnews/search/public/nsIMsgFilterPlugin.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterPlugin.idl>`_

This interface is still very much under development, and is not yet stable.

Properties
==========

shouldDownloadAllHeaders
------------------------

``readonly attribute boolean shouldDownloadAllHeaders``

Some protocols (ie IMAP) can, as an optimization, avoid
downloading all message header lines.  If your plugin doesn't need
any more than the minimal set, it can return false for this attribute.

Methods
=======

shutdown
--------

``void shutdown()``

Do any necessary cleanup: flush and close any open files, etc.

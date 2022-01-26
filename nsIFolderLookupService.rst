======================
nsIFolderLookupService
======================

`mailnews/base/public/nsIFolderLookupService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIFolderLookupService.idl>`_

This service provides a way to lookup any nsIMsgFolder.

When looking up folders by URL, note that the URL must be encoded to be a
valid folder URL. Of particular note are the following requirements:
- invalid characters in paths must be percent-encoded
- the URL MUST NOT have a trailing slash (excepting root folders)
- the case must match the expected value exactly
An example of a valid URL is thus:
imap://someuser%40google.com@imap.google.com/INBOX

The contractid for this service is "@mozilla.org/mail/folder-lookup;1".

Methods
=======

getFolderForURL
---------------

``nsIMsgFolder getFolderForURL(aUrl)``

Returns a folder with the given URL or null if no such folder exists.

Parameters
^^^^^^^^^^

* in AUTF8String aUrl

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

getOrCreateFolderForURL
-----------------------

``nsIMsgFolder getOrCreateFolderForURL(aUrl)``

Returns a folder with the given URL.
Will happily create and return an invalid (unparented) folder.
Will return null if aUrl is not a folder url.
NOTE: don't use this for new code! It's here purely to help
transition away from RDF-based folder creation.

Parameters
^^^^^^^^^^

* in AUTF8String aUrl

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

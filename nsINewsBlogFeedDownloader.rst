=========================
nsINewsBlogFeedDownloader
=========================

`mailnews/local/public/nsINewsBlogFeedDownloader.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsINewsBlogFeedDownloader.idl>`_


Methods
=======

downloadFeed
------------

``void downloadFeed(aFolder, aUrlListener, aIsBiff, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIUrlListener` aUrlListener
* in bool aIsBiff
* in :doc:`nsIMsgWindow` aMsgWindow

subscribeToFeed
---------------

``void subscribeToFeed(aUrl, aFolder, aMsgWindow)``

A convient method to subscribe to feeds without going through the Subscribe
dialog; used by drag and drop and commandline.

Parameters
^^^^^^^^^^

* in string aUrl
* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgWindow` aMsgWindow

updateSubscriptionsDS
---------------------

``void updateSubscriptionsDS(aFolder, aOrigFolder, aAction)``

Called when the RSS Incoming Server detects a change to an RSS folder name,
such as delete (move to trash), move/copy, or rename. We then need to update
the feeds.rdf subscriptions data source.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgFolder` aOrigFolder
* in string aAction

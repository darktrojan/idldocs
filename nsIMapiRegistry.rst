===============
nsIMapiRegistry
===============

`mailnews/base/public/nsIMapiRegistry.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMapiRegistry.idl>`_

This interface provides support for registering Mozilla as the default
Mail Client. This interface can also be used to get/set the user preference
for the default Mail Client.


Properties
==========

isDefaultMailClient
-------------------

``attribute boolean isDefaultMailClient``

This is set to TRUE if Mozilla is the default mail application

isDefaultNewsClient
-------------------

``attribute boolean isDefaultNewsClient``

isDefaultFeedClient
-------------------

``attribute boolean isDefaultFeedClient``

showDialog
----------

``readonly attribute boolean showDialog``

This is set TRUE only once per session.

Methods
=======

showMailIntegrationDialog
-------------------------

``void showMailIntegrationDialog(parentWindow)``

This will bring the dialog asking the user if he/she wants to set
Mozilla as default Mail Client.
Call this only if Mozilla is not the default Mail client

Parameters
^^^^^^^^^^

* in mozIDOMWindowProxy parentWindow

registerMailAndNewsClient
-------------------------

``void registerMailAndNewsClient()``

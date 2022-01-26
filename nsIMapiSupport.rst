==============
nsIMapiSupport
==============

`mailnews/mapi/mapihook/public/nsIMapiSupport.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mapi/mapihook/public/nsIMapiSupport.idl>`_

This interface provides support for registering Mozilla as a COM component
for extending the use of Mail/News through Simple MAPI.


Methods
=======

initializeMAPISupport
---------------------

``void initializeMAPISupport()``

Initiates MAPI support

shutdownMAPISupport
-------------------

``void shutdownMAPISupport()``

Shuts down the MAPI support

registerServer
--------------

``void registerServer()``

registerServer - register the mapi DLL with the desktop
Typically called by the window shell service when we are
made the default mail app

unRegisterServer
----------------

``void unRegisterServer()``

unRegisterServer - unregister the mapi DLL with the desktop
Typically called by the window shell service when we are
removed as the default mail app.

============
msgIOverride
============

`mailnews/jsaccount/public/msgIOverride.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/jsaccount/public/msgIOverride.idl>`_

Mailnews code typically has a C++ base class for objects, which is then
specialized for each account type with a C++ subclass of the base class.

This interface provides the ability of JavaScript-based account
implementations to use the same C++ base classes as core objects, but
use JavaScript to override methods instead of C++.

Properties
==========

methodsToDelegate
-----------------

``attribute msgIDelegateList methodsToDelegate``


A list of methods in the C++ base class that will be delegated to the JS
delegate. This is calculated once, and then a fixed value is set to
all subsequent instances so that it does not need to be recalculated each
time. If the value has not yet been set, this will return a new instance.

jsDelegate
----------

``attribute nsISupports jsDelegate``

JavaScript-based xpcom object that overrides C++ methods.

cppBase
-------

``readonly attribute nsISupports cppBase``

C++ class used to implement default functionality. This is used when
JavaScript methods want to call the base class default action, bypassing a
possible JS override.

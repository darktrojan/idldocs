================
msgIDelegateList
================

`mailnews/jsaccount/public/msgIDelegateList.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/jsaccount/public/msgIDelegateList.idl>`_

This interface provides a list of methods that should be delegated to
a JsObject rather than a C++ XPCOM base object in JsAccount classes.

Methods
=======

add
---

``void add(aMethod)``

Parameters
^^^^^^^^^^

* in ACString aMethod

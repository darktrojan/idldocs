==============
nsIMsgMailView
==============

`mailnews/extensions/mailviews/nsIMsgMailView.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/mailviews/nsIMsgMailView.idl>`_


Properties
==========

mailViewName
------------

``attribute wstring mailViewName``

prettyName
----------

``readonly attribute wstring prettyName``

searchTerms
-----------

``attribute Array<nsIMsgSearchTerm> searchTerms``

Methods
=======

appendTerm
----------

``void appendTerm(term)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchTerm` term

createTerm
----------

``nsIMsgSearchTerm createTerm()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgSearchTerm`

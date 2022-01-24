======================
nsIAbDirSearchListener
======================

Listener callbacks for addressbook nsIAbDirectory searches and queries.

Methods
=======

onSearchFoundCard
-----------------

Invoked for each matching result found by the search.

Parameters
^^^^^^^^^^

* ``in nsIAbCard aCard``

Return value
^^^^^^^^^^^^

* ``void``

onSearchFinished
----------------

Invoked when the search finishes.

Parameters
^^^^^^^^^^

* ``in nsresult status``
* ``in bool complete``
* ``in nsITransportSecurityInfo secInfo``
* ``in ACString location``

Return value
^^^^^^^^^^^^

* ``void``

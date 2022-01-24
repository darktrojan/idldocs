======================
nsIAbDirSearchListener
======================

Listener callbacks for addressbook nsIAbDirectory searches and queries.

Methods
=======

onSearchFoundCard
-----------------

``void onSearchFoundCard(aCard)``

Invoked for each matching result found by the search.

Parameters
^^^^^^^^^^

* in :doc:`nsIAbCard` aCard

onSearchFinished
----------------

``void onSearchFinished(status, complete, secInfo, location)``

Invoked when the search finishes.

Parameters
^^^^^^^^^^

* in nsresult status
* in bool complete
* in :doc:`nsITransportSecurityInfo` secInfo
* in ACString location

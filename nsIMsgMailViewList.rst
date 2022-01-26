==================
nsIMsgMailViewList
==================

`mailnews/extensions/mailviews/nsIMsgMailViewList.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/extensions/mailviews/nsIMsgMailViewList.idl>`_


Properties
==========

mailViewCount
-------------

``readonly attribute unsigned long mailViewCount``

Methods
=======

getMailViewAt
-------------

``nsIMsgMailView getMailViewAt(mailViewIndex)``

Parameters
^^^^^^^^^^

* in unsigned long mailViewIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgMailView`

addMailView
-----------

``void addMailView(mailView)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailView` mailView

removeMailView
--------------

``void removeMailView(mailView)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailView` mailView

createMailView
--------------

``nsIMsgMailView createMailView()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgMailView`

save
----

``void save()``

======================
nsIAbBooleanExpression
======================

`mailnews/addrbook/public/nsIAbBooleanExpression.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbBooleanExpression.idl>`_

N Boolean expression type

Supports Unary Binary and N boolean expressions

An operation represents a node in a boolean
expression tree which may contain one or more
child conditions or expressions


Properties
==========

operation
---------

``attribute nsAbBooleanOperationType operation``

The boolean operation to be applied to
results of all evaluated expressions


expressions
-----------

``attribute Array<nsISupports> expressions``

List of peer expressions

e1 [op] e2 [op] .... en


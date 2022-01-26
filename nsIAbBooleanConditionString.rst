===========================
nsIAbBooleanConditionString
===========================

`mailnews/addrbook/public/nsIAbBooleanExpression.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbBooleanExpression.idl>`_

String condition

A string condition represents a leaf node in a
boolean expression tree and represents
test which will return TRUE or FALSE

Condition is an expression which is a
leaf node in a boolean expression tree


Properties
==========

condition
---------

``attribute nsAbBooleanConditionType condition``

The condition for how the a value
should be compared


name
----

``attribute string name``

The lhs of the condition

Represents a property name which
should be evaluated to obtain the
lhs.


value
-----

``attribute wstring value``

The rhs of the condition

<name> [condition] value


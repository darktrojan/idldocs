==============
nsILDAPControl
==============

XPCOM representation of the C SDK LDAPControl structure.

Properties
==========

oid
---

``attribute ACString oid``

Control type, represented as a string.

@exceptions   none

value
-----

``attribute nsILDAPBERValue value``

The data associated with a control, if any.  To specify that no data
is to be associated with the control, don't set this at all (which
is equivalent to setting it to null).

@note Specifying a zero-length value is not currently supported.  At some
date, setting this to an nsILDAPBERValue which has not had any of the
set methods called will be the appropriate way to do that.

@exceptions   none

isCritical
----------

``attribute boolean isCritical``

Should the client or server abort if the control is not understood?
Should be set to false for server controls used in abandon and unbind
operations, since those have no server response.

@exceptions   none

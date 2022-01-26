=============
nsILDAPErrors
=============

`mailnews/addrbook/public/nsILDAPErrors.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsILDAPErrors.idl>`_

Error codes used in the LDAP XPCOM SDK.

Taken from the Mozilla C SDK's ldap.h include file, these should be
the same as those specified in the draft-ietf-ldapext-ldap-c-api-04.txt
Internet Draft.

The only good documentation I'm aware of for these error codes is
at <http://docs.iplanet.com/docs/manuals/directory.html#SDKC>.
Unfortunately, this does not currently seem to be available under any
open source license, so I can't include that documentation here as
doxygen comments.


Constants
=========

SUCCESS
-------

**Type**: ``long``

**Value**: ``0``


OPERATIONS_ERROR
----------------

**Type**: ``long``

**Value**: ``1``


PROTOCOL_ERROR
--------------

**Type**: ``long``

**Value**: ``2``


TIMELIMIT_EXCEEDED
------------------

**Type**: ``long``

**Value**: ``3``


SIZELIMIT_EXCEEDED
------------------

**Type**: ``long``

**Value**: ``4``


COMPARE_FALSE
-------------

**Type**: ``long``

**Value**: ``5``


COMPARE_TRUE
------------

**Type**: ``long``

**Value**: ``6``


STRONG_AUTH_NOT_SUPPORTED
-------------------------

**Type**: ``long``

**Value**: ``7``


STRONG_AUTH_REQUIRED
--------------------

**Type**: ``long``

**Value**: ``8``


PARTIAL_RESULTS
---------------

**Type**: ``long``

**Value**: ``9``

UMich LDAPv2 extension

REFERRAL
--------

**Type**: ``long``

**Value**: ``10``

new in LDAPv3

ADMINLIMIT_EXCEEDED
-------------------

**Type**: ``long``

**Value**: ``11``

new in LDAPv3

UNAVAILABLE_CRITICAL_EXTENSION
------------------------------

**Type**: ``long``

**Value**: ``12``

new in LDAPv3

CONFIDENTIALITY_REQUIRED
------------------------

**Type**: ``long``

**Value**: ``13``

new in LDAPv3

SASL_BIND_IN_PROGRESS
---------------------

**Type**: ``long``

**Value**: ``14``

new in LDAPv3

NO_SUCH_ATTRIBUTE
-----------------

**Type**: ``long``

**Value**: ``16``


UNDEFINED_TYPE
--------------

**Type**: ``long``

**Value**: ``17``


INAPPROPRIATE_MATCHING
----------------------

**Type**: ``long``

**Value**: ``18``


CONSTRAINT_VIOLATION
--------------------

**Type**: ``long``

**Value**: ``19``


TYPE_OR_VALUE_EXISTS
--------------------

**Type**: ``long``

**Value**: ``20``


INVALID_SYNTAX
--------------

**Type**: ``long``

**Value**: ``21``


NO_SUCH_OBJECT
--------------

**Type**: ``long``

**Value**: ``32``


ALIAS_PROBLEM
-------------

**Type**: ``long``

**Value**: ``33``


INVALID_DN_SYNTAX
-----------------

**Type**: ``long``

**Value**: ``34``


IS_LEAF
-------

**Type**: ``long``

**Value**: ``35``

not used in LDAPv3

ALIAS_DEREF_PROBLEM
-------------------

**Type**: ``long``

**Value**: ``36``


INAPPROPRIATE_AUTH
------------------

**Type**: ``long``

**Value**: ``48``


INVALID_CREDENTIALS
-------------------

**Type**: ``long``

**Value**: ``49``


INSUFFICIENT_ACCESS
-------------------

**Type**: ``long``

**Value**: ``50``


BUSY
----

**Type**: ``long``

**Value**: ``51``


UNAVAILABLE
-----------

**Type**: ``long``

**Value**: ``52``


UNWILLING_TO_PERFORM
--------------------

**Type**: ``long``

**Value**: ``53``


LOOP_DETECT
-----------

**Type**: ``long``

**Value**: ``54``


SORT_CONTROL_MISSING
--------------------

**Type**: ``long``

**Value**: ``60``

server side sort extension

INDEX_RANGE_ERROR
-----------------

**Type**: ``long``

**Value**: ``61``

VLV extension

NAMING_VIOLATION
----------------

**Type**: ``long``

**Value**: ``64``


OBJECT_CLASS_VIOLATION
----------------------

**Type**: ``long``

**Value**: ``65``


NOT_ALLOWED_ON_NONLEAF
----------------------

**Type**: ``long``

**Value**: ``66``


NOT_ALLOWED_ON_RDN
------------------

**Type**: ``long``

**Value**: ``67``


ALREADY_EXISTS
--------------

**Type**: ``long``

**Value**: ``68``


NO_OBJECT_CLASS_MODS
--------------------

**Type**: ``long``

**Value**: ``69``


RESULTS_TOO_LARGE
-----------------

**Type**: ``long``

**Value**: ``70``

reserved CLDAP

AFFECTS_MULTIPLE_DSAS
---------------------

**Type**: ``long``

**Value**: ``71``

new in LDAPv3

OTHER
-----

**Type**: ``long``

**Value**: ``80``


SERVER_DOWN
-----------

**Type**: ``long``

**Value**: ``81``


LOCAL_ERROR
-----------

**Type**: ``long``

**Value**: ``82``


ENCODING_ERROR
--------------

**Type**: ``long``

**Value**: ``83``


DECODING_ERROR
--------------

**Type**: ``long``

**Value**: ``84``


TIMEOUT
-------

**Type**: ``long``

**Value**: ``85``


AUTH_UNKNOWN
------------

**Type**: ``long``

**Value**: ``86``


FILTER_ERROR
------------

**Type**: ``long``

**Value**: ``87``


USER_CANCELLED
--------------

**Type**: ``long``

**Value**: ``88``


PARAM_ERROR
-----------

**Type**: ``long``

**Value**: ``89``


NO_MEMORY
---------

**Type**: ``long``

**Value**: ``90``


CONNECT_ERROR
-------------

**Type**: ``long``

**Value**: ``91``


NOT_SUPPORTED
-------------

**Type**: ``long``

**Value**: ``92``

new in LDAPv3

CONTROL_NOT_FOUND
-----------------

**Type**: ``long``

**Value**: ``93``

new in LDAPv3

NO_RESULTS_RETURNED
-------------------

**Type**: ``long``

**Value**: ``94``

new in LDAPv3

MORE_RESULTS_TO_RETURN
----------------------

**Type**: ``long``

**Value**: ``95``

new in LDAPv3

CLIENT_LOOP
-----------

**Type**: ``long``

**Value**: ``96``

new in LDAPv3

REFERRAL_LIMIT_EXCEEDED
-----------------------

**Type**: ``long``

**Value**: ``97``

new in LDAPv3

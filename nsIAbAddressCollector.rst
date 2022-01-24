=====================
nsIAbAddressCollector
=====================

nsIAbAddressCollector is the interface to the address collecter service.
It will save and update the supplied addresses into the address book
specified by the "mail.collect_addressbook" pref.

Methods
=======

collectAddress
--------------

Collects email addresses into the address book.
If a card already exists for the email, the first/last/display names
will be updated if they are supplied alongside the address.
If a card does not exist for the email it will be created if aCreateCard
is true.

@param  aAddresses  The list of emails (in standard header format)
to collect into the address book.
@param  aCreateCard Set to true if a card should be created if the
email address doesn't exist.
@param  aSendFormat The send format to save for the card. See
nsIAbPreferMailFormat for values. If updating a card
this value will only be changed if the current value
for the card is "unknown".

Parameters
^^^^^^^^^^

* ``in AUTF8String aAddresses``
* ``in boolean aCreateCard``
* ``in unsigned long aSendFormat``

Return value
^^^^^^^^^^^^

* ``void``

collectSingleAddress
--------------------

Collects a single name and email address into the address book.
By default, it saves the address without checking for an existing one.
See collectAddress for the general implementation.

@param  aEmail         The email address to collect.
@param  aDisplayName   The display name associated with the email address.
@param  aCreateCard    Set to true if a card should be created if the
email address doesn't exist (ignored if
aSkipCheckExisting is true).
@param  aSendFormat    The send format to save for the card. See
nsIAbPreferMailFormat for values. If updating a card
this value will only be changed if the current value
for the card is "unknown".
@param  aSkipCheckExisting Optional parameter, if this is set then the
implementation will skip checking for an
existing card, and just create a new card.

Parameters
^^^^^^^^^^

* ``in AUTF8String aEmail``
* ``in AUTF8String aDisplayName``
* ``in boolean aCreateCard``
* ``in unsigned long aSendFormat``
* ``in boolean aSkipCheckExisting``

Return value
^^^^^^^^^^^^

* ``void``

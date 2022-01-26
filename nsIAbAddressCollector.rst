=====================
nsIAbAddressCollector
=====================

`mailnews/addrbook/public/nsIAbAddressCollector.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbAddressCollector.idl>`_

nsIAbAddressCollector is the interface to the address collecter service.
It will save and update the supplied addresses into the address book
specified by the "mail.collect_addressbook" pref.

Methods
=======

collectAddress
--------------

``void collectAddress(aAddresses, aCreateCard, aSendFormat)``

Collects email addresses into the address book.
If a card already exists for the email, the first/last/display names
will be updated if they are supplied alongside the address.
If a card does not exist for the email it will be created if aCreateCard
is true.

Parameters
^^^^^^^^^^

* in AUTF8String aAddresses

  The list of emails (in standard header format)
  to collect into the address book.
* in boolean aCreateCard

  Set to true if a card should be created if the
  email address doesn't exist.
* in unsigned long aSendFormat

  The send format to save for the card. See
  nsIAbPreferMailFormat for values. If updating a card
  this value will only be changed if the current value
  for the card is "unknown".

collectSingleAddress
--------------------

``void collectSingleAddress(aEmail, aDisplayName, aCreateCard, aSendFormat, aSkipCheckExisting)``

Collects a single name and email address into the address book.
By default, it saves the address without checking for an existing one.
See collectAddress for the general implementation.

Parameters
^^^^^^^^^^

* in AUTF8String aEmail

  The email address to collect.
* in AUTF8String aDisplayName

  The display name associated with the email address.
* in boolean aCreateCard

  Set to true if a card should be created if the
  email address doesn't exist (ignored if
  aSkipCheckExisting is true).
* in unsigned long aSendFormat

  The send format to save for the card. See
  nsIAbPreferMailFormat for values. If updating a card
  this value will only be changed if the current value
  for the card is "unknown".
* in boolean aSkipCheckExisting

  Optional parameter, if this is set then the
  implementation will skip checking for an
  existing card, and just create a new card.

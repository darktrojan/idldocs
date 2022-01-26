==============
nsIMsgIdentity
==============

`mailnews/base/public/nsIMsgIdentity.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgIdentity.idl>`_

This interface contains all the personal outgoing mail information
for a given person.
Each identity is identified by a key, which is the <id> string in
the identity preferences, such as in mail.identity.<id>.replyTo.

Constants
=========

singleArchiveFolder
-------------------

**Type**: ``long``

**Value**: ``0``


perYearArchiveFolders
---------------------

**Type**: ``long``

**Value**: ``1``


perMonthArchiveFolders
----------------------

**Type**: ``long``

**Value**: ``2``


Properties
==========

key
---

``attribute ACString key``

Internal preferences ID.

label
-----

``attribute AString label``

Label describing this identity. May be empty.

identityName
------------

``readonly attribute AString identityName``

Pretty display name to identify this specific identity. Will return a
composed string like "fullname <email> (label)".

fullName
--------

``attribute AString fullName``

User's full name, i.e. John Doe.

email
-----

``attribute ACString email``

User's e-mail address, i.e. john@doe.com.

catchAll
--------

``attribute boolean catchAll``

Do we use multiple e-mail addresses (like Catch-All) with this identity?

catchAllHint
------------

``attribute AUTF8String catchAllHint``

Hint for when to use this identity as catch all. It is a comma separated
list of things to look for delivery in headers when replying to a message
that was not directly addressed to a matching identity.

fullAddress
-----------

``readonly attribute AString fullAddress``

Formats fullName and email into the proper string to use as sender:
name <email>

replyTo
-------

``attribute AUTF8String replyTo``

Optional replyTo address, i.e. johnNOSPAM@doe.com.

organization
------------

``attribute AString organization``

Optional organization.

composeHtml
-----------

``attribute boolean composeHtml``

Should we compose with HTML by default?

attachSignature
---------------

``attribute boolean attachSignature``

Should we attach a signature from file?

attachVCard
-----------

``attribute boolean attachVCard``

Should we attach a vcard by default?

autoQuote
---------

``attribute boolean autoQuote``

Should we automatically quote the original message?

replyOnTop
----------

``attribute long replyOnTop``

What should our quoting preference be?

sigBottom
---------

``attribute boolean sigBottom``

Should our signature be at the end of the quoted text when replying
above it?

sigOnForward
------------

``attribute boolean sigOnForward``

Include a signature when forwarding a message?

sigOnReply
----------

``attribute boolean sigOnReply``

Include a signature when replying to a message?

signature
---------

``attribute nsIFile signature``

The current signature file.

signatureDate
-------------

``attribute long signatureDate``

Modification time of the signature file.

htmlSigText
-----------

``attribute AString htmlSigText``

Signature text if not read from file; format depends on htmlSigFormat.

htmlSigFormat
-------------

``attribute boolean htmlSigFormat``

Does htmlSigText contain HTML? Use plain text if false.

suppressSigSep
--------------

``attribute boolean suppressSigSep``

Suppress the double-dash signature separator

escapedVCard
------------

``attribute ACString escapedVCard``

The encoded string representing the vcard.

doFcc
-----

``attribute boolean doFcc``

fccFolder
---------

``attribute AUTF8String fccFolder``

fccReplyFollowsParent
---------------------

``attribute boolean fccReplyFollowsParent``

fccFolderPickerMode
-------------------

``attribute ACString fccFolderPickerMode``

@{
these attributes control whether the special folder pickers for
fcc, drafts,archives, and templates are set to pick between servers
(e.g., Sent on accountName) or to pick any folder on any account.
"0" means choose between servers; "1" means use the full folder picker.

draftsFolderPickerMode
----------------------

``attribute ACString draftsFolderPickerMode``

archivesFolderPickerMode
------------------------

``attribute ACString archivesFolderPickerMode``

tmplFolderPickerMode
--------------------

``attribute ACString tmplFolderPickerMode``

bccSelf
-------

``attribute boolean bccSelf``

@} */

bccOthers
---------

``attribute boolean bccOthers``

bccList
-------

``attribute ACString bccList``

doCc
----

``attribute boolean doCc``

doCcList
--------

``attribute AUTF8String doCcList``

doBcc
-----

``attribute boolean doBcc``

doBccList
---------

``attribute AUTF8String doBccList``

draftFolder
-----------

``attribute AUTF8String draftFolder``

@{
URIs for the special folders (drafts, templates, archive)

archiveFolder
-------------

``attribute AUTF8String archiveFolder``

stationeryFolder
----------------

``attribute AUTF8String stationeryFolder``

archiveEnabled
--------------

``attribute boolean archiveEnabled``

@} */

archiveGranularity
------------------

``attribute long archiveGranularity``

@{
This attribute and constants control the granularity of sub-folders of the
Archives folder - either messages go in the single archive folder, or a
yearly archive folder, or in a monthly archive folder with a yearly
parent folder. If the server doesn't support folders that both contain
messages and have sub-folders, we will ignore this setting.

archiveKeepFolderStructure
--------------------------

``attribute boolean archiveKeepFolderStructure``

showSaveMsgDlg
--------------

``attribute boolean showSaveMsgDlg``

@} */

directoryServer
---------------

``attribute ACString directoryServer``

overrideGlobalPref
------------------

``attribute boolean overrideGlobalPref``

autocompleteToMyDomain
----------------------

``attribute boolean autocompleteToMyDomain``

If this is false, don't append the user's domain
to an autocomplete address with no matches

valid
-----

``attribute boolean valid``

valid determines if the UI should use this identity
and the wizard uses this to determine whether or not
to ask the user to complete all the fields

smtpServerKey
-------------

``attribute ACString smtpServerKey``

the preferred smtp server for this identity.
if this is set, this the smtp server that should be used
for the message send

requestReturnReceipt
--------------------

``readonly attribute boolean requestReturnReceipt``

default request for return receipt option for this identity
if this is set, the Return Receipt menu item on the compose
window will be checked

receiptHeaderType
-----------------

``readonly attribute long receiptHeaderType``

requestDSN
----------

``readonly attribute boolean requestDSN``

default request for DSN option for this identity
if this is set, the DSN menu item on the compose
window will be checked

Methods
=======

clearAllValues
--------------

``void clearAllValues()``

this is really dangerous. this destroys all pref values
do not call this unless you know what you're doing!

copy
----

``void copy(identity)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity

getUnicharAttribute
-------------------

``AString getUnicharAttribute(name)``

these generic getter / setters, useful for extending mailnews
note, these attributes persist across sessions

Parameters
^^^^^^^^^^

* in string name

Return value
^^^^^^^^^^^^

* AString

setUnicharAttribute
-------------------

``void setUnicharAttribute(name, value)``

Parameters
^^^^^^^^^^

* in string name
* in AString value

getCharAttribute
----------------

``ACString getCharAttribute(name)``

Parameters
^^^^^^^^^^

* in string name

Return value
^^^^^^^^^^^^

* ACString

setCharAttribute
----------------

``void setCharAttribute(name, value)``

Parameters
^^^^^^^^^^

* in string name
* in ACString value

getBoolAttribute
----------------

``boolean getBoolAttribute(name)``

Parameters
^^^^^^^^^^

* in string name

Return value
^^^^^^^^^^^^

* boolean

setBoolAttribute
----------------

``void setBoolAttribute(name, value)``

Parameters
^^^^^^^^^^

* in string name
* in boolean value

getIntAttribute
---------------

``long getIntAttribute(name)``

Parameters
^^^^^^^^^^

* in string name

Return value
^^^^^^^^^^^^

* long

setIntAttribute
---------------

``void setIntAttribute(name, value)``

Parameters
^^^^^^^^^^

* in string name
* in long value

toString
--------

``AString toString()``

Return value
^^^^^^^^^^^^

* AString

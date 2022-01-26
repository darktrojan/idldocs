==================
nsIAbLDAPDirectory
==================

`mailnews/addrbook/public/nsIAbLDAPDirectory.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/addrbook/public/nsIAbLDAPDirectory.idl>`_

XXX This should really inherit from nsIAbDirectory, and some day it will.
But for now, doing that complicates implementation.

Properties
==========

replicationFileName
-------------------

``attribute ACString replicationFileName``

The Replication File Name to use.

protocolVersion
---------------

``attribute unsigned long protocolVersion``

The version of LDAP protocol in use.

saslMechanism
-------------

``attribute ACString saslMechanism``

The SASL mechanism to use to authenticate to the LDAP server
If this is an empty string, then a simple bind will be performed
A non-zero string is assumed to be the name of the SASL mechanism.
Currently the only supported mechanism is GSSAPI

authDn
------

``attribute AUTF8String authDn``

The AuthDN to use to access the server.

maxHits
-------

``attribute long maxHits``

The maximum number of matches that the server will return per a search.

lastChangeNumber
----------------

``attribute long lastChangeNumber``

The Last Change Number used for replication.

dataVersion
-----------

``attribute ACString dataVersion``

The LDAP server's scoping of the lastChangeNumber.

attributeMap
------------

``readonly attribute nsIAbLDAPAttributeMap attributeMap``

The attribute map that is associated with this directory's server.

lDAPURL
-------

``attribute nsILDAPURL lDAPURL``

The LDAP URL for this directory. Note that this differs from
nsIAbDirectory::URI. This attribute will give you a true ldap
url, e.g. ldap://localhost:389/ whereas the uri will give you the
directories rdf uri, e.g. moz-abldapdirectory://<pref base name>/.

replicationFile
---------------

``readonly attribute nsIFile replicationFile``

The replication (offline) file that this database uses.

rdnAttributes
-------------

``attribute ACString rdnAttributes``

The LDAP attributes used to build the Relative Distinguished Name
of new cards, in the form of a comma separated list.

The default is to use the common name (cn) attribute.

objectClasses
-------------

``attribute ACString objectClasses``

The LDAP objectClass values added to cards when they are created/added,
in the form of a comma separated list.

The default is to use the following classes:
top,person,organizationalPerson,inetOrgPerson,mozillaAbPersonAlpha

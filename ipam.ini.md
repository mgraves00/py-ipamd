# IPAM.INI

## Description

The ipam.ini instrusts the ipamctl(5) and ipamd(5) 

## Section

### Server keys

	listen		ip address for the ipamd(5) server to listen on (required)
	port		port for the ipamd(5) server to listen on (required)
	user		user to change to with running as daemon (optional)
	logfile		path to write the logfile to (optional) (default:/var/log/ipamd.log)

### Database keys

	type		type of datase connection. for ipamd only sqlite3 is valid options: http, sqlite3
	server		ip of the server to connect to (only for type http)
	port		port for the server to connect to (only for type http)
	path		path for the database file (only for type sqlite3)

### Role Based Access Control

Section titles are prefeced with 'rbac_' and the user name. If a restriction is not specified
then all options are assume to be permitted.  Restrictions should be separated by commas.
Restrictions are additative, meaning if someone should be restricted to manuiplate records in
example.com domain but only be able to view example.net then there needs to be 2 rbac section
with different names.

	key			The API key associated with the user
	actions		Allowed actions: view, create, update, delete
	domains		Allowed domains to update.  Higher level domains permit subdomains.
	resources	Allowed resources: domain, record, network
	types		Allowed record types: A, AAAA, etc.

## Examples

### Config for ipamctl with remote connection to ipamd
	[database]
	type=http
	server=127.0.0.1
	port=8000
	apikey=abc123:keep_me_secret

### Config for ipamctl with local db
	[database]
	type=sqlite3
	path=/var/db/ipam.db

### Config for ipamd
	# can only update records in example.com domain
	[rbac_abc123]
	key=keep_me_secret
	domains=example.com
	resources=records

	# can do everything
	[rbac_superadmin]
	key=really_secret_key

	[database]
	type=sqlite3
	path=/var/db/ipam.db

	[server]
	listen=127.0.0.1
	port=8000
	user=_ipam

## Also See
	ipamctl(7), ipamd(7)


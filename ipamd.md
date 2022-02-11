# IPAMD

## Synopsis

	ipamd [-dh] [-c file]

## Description

The ipamd utilitiy allows remote ipamctl client to interaction with the IPAM database.  The ipam.ini config file is searched for in /etc/ipam.ini, ~/.ipam.ini and the path specificed by -c.

The options are as follows:

	-c		Specifiy an alternat config file to read
	-d		run daemon in forground mode
	-h		Help screen

## Notes

If using the user= option to have the daemon change to an unpriv user make sure that the the unpriv user has +rw to the directory the database is stored in.

### Security

The APIkey does not secure the traffic in transit.  If transit security is required then a web server with TLS enabled should be used to proxy the connection.

## Also See
	ipam.ini(5), ipamctl(7)


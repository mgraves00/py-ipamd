#
COMMENT =		daemon for manipulating simple IPAM database from clients

V =1.0.8
MODPY_EGG_VERSION =	${V}
#REVISION =		3
DISTNAME =		py-ipamd-${V}
PKGNAME =		py-ipamd-${V}

CATEGORIES =		net

HOMEPATH =		https://github.com/mgraves00/py-ipamd/

MAINTAINER =		Michael Graves

SITES = 		https://github.com/mgraves00/py-ipamd/releases/download/v${V}/

# BSD 3 clause
PERMIT_PACKAGE =	Yes
PERMIT_DISTFILES =	Yes

MODULES =		lang/python

MODPY_PI =		No
#MODPY_PYBUILD = 	setuptools

CONFIGURE_STYLE =	none
NO_BUILD =		Yes
NO_TEST =		Yes

FLAVOR =		python3
FLAVORS =		python3
RUN_DEPENDS =		net/py-libipam${MODPY_FLAVOR} \
			sysutils/py-daemon${MODPY_FLAVOR}

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/ipamd ${PREFIX}/sbin/
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/ipamd
	${INSTALL_DATA} ${WRKSRC}/ipam.ini.md ${PREFIX}/share/examples/ipamd
	${INSTALL_DATA} ${WRKSRC}/ipamd.md ${PREFIX}/share/examples/ipamd

.include <bsd.port.mk>

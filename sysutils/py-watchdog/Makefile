COMMENT =		filesystem event monitoring

# XXX restrictive version spec in spyder3
MODPY_EGG_VERSION =	1.0.2
DISTNAME =		watchdog-${MODPY_EGG_VERSION}
PKGNAME =		py-${DISTNAME}

CATEGORIES =		sysutils

# Apache 2.0
PERMIT_PACKAGE =	Yes

MODULES =		lang/python

FLAVORS =		python3
FLAVOR =		python3

MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools

TEST_DEPENDS =		devel/py-test-cov${MODPY_FLAVOR} \
			devel/py-argh${MODPY_FLAVOR} \
			devel/py-flaky${MODPY_FLAVOR} \
			textproc/py-yaml${MODPY_FLAVOR}

.include <bsd.port.mk>

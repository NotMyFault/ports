COMMENT =		OAuth library support for python-requests

MODPY_EGG_VERSION =	1.3.1
DISTNAME =		requests-oauthlib-${MODPY_EGG_VERSION}
PKGNAME =		py-${DISTNAME}
REVISION =		1

CATEGORIES =		www

HOMEPAGE =		https://github.com/requests/requests-oauthlib

# ISC
PERMIT_PACKAGE =	Yes

MODULES =		lang/python

RUN_DEPENDS =		security/py-oauthlib${MODPY_FLAVOR} \
			www/py-requests${MODPY_FLAVOR}

TEST_DEPENDS =		devel/py-mock${MODPY_FLAVOR} \
			www/py-requests-mock${MODPY_FLAVOR}

MODPY_PI =		Yes
MODPY_PYBUILD =		setuptools
# the tests make connections to http://httpbin.org

FLAVORS =		python3
FLAVOR =		python3

pre-test:
	rm -rf ${WRKSRC}/tests/__pycache__

.include <bsd.port.mk>

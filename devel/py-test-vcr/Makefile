COMMENT =		plugin for managing VCR.py cassettes

MODPY_EGG_VERSION =	1.0.2
DISTNAME =		pytest-vcr-${MODPY_EGG_VERSION}
PKGNAME =		py-test-vcr-${MODPY_EGG_VERSION}
REVISION =		4

CATEGORIES =		devel

HOMEPAGE =		https://github.com/ktosiek/pytest-vcr

MAINTAINER =		Pamela Mosiejczuk <pamela@openbsd.org>

# MIT
PERMIT_PACKAGE =	Yes

MODULES =		lang/python
MODPY_PYBUILD =		setuptools
MODPY_PI =		Yes

FLAVORS =		python3
FLAVOR =		python3

RUN_DEPENDS =		www/py-vcrpy${MODPY_FLAVOR}

#tests not included in PyPI sdist, an issue is open upstream
.include <bsd.port.mk>

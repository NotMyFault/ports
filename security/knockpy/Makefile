COMMENT =	subdomain scanner

MODPY_EGG_VERSION =	6.1.0

DISTNAME =	knockpy-${MODPY_EGG_VERSION}

GH_ACCOUNT =	guelfoweb
GH_PROJECT =	knock
GH_TAGNAME =	${MODPY_EGG_VERSION}

CATEGORIES =	security

MAINTAINER =	Rafael Sadowski <rsadowski@openbsd.org>

# GPLv3+
PERMIT_PACKAGE=	Yes

MODULES =		lang/python

MODPY_PYBUILD =	setuptools

RUN_DEPENDS =		devel/py-colorama${MODPY_FLAVOR} \
			graphics/py-matplotlib${MODPY_FLAVOR} \
			math/py-networkx${MODPY_FLAVOR} \
			www/py-beautifulsoup4${MODPY_FLAVOR} \
			www/py-requests${MODPY_FLAVOR} \
			x11/py-qt5${MODPY_FLAVOR}

.include <bsd.port.mk>

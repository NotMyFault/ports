COMMENT=	common base representation of Python source code

# py-astroid and pylint usually need keeping in-sync
MODPY_EGG_VERSION=	3.0.1
DISTNAME=	astroid-${MODPY_EGG_VERSION}
PKGNAME=	py-${DISTNAME}
CATEGORIES=	devel

# LGPLv2.1+
PERMIT_PACKAGE=	Yes

MODULES=	lang/python

FLAVORS=	python3
FLAVOR=		python3

MODPY_PI=	Yes
MODPY_PYBUILD=	setuptools

RUN_DEPENDS=	devel/py-typing-extensions${MODPY_FLAVOR}

.include <bsd.port.mk>

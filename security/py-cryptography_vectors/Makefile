COMMENT=	test vectors for py-cryptography

MODPY_EGG_VERSION=	41.0.1
DISTNAME=	cryptography_vectors-${MODPY_EGG_VERSION}
PKGNAME=	${MODPY_PY_PREFIX}${DISTNAME}
CATEGORIES=	security

HOMEPAGE=	https://cryptography.io/

# dual: BSD or Apache 2
PERMIT_PACKAGE=	Yes

MODULES=	lang/python
MODPY_PYBUILD=	setuptools
MODPY_PI=	Yes
MODPY_PI_DIR=	c/cryptography-vectors
NO_TEST=	Yes

FLAVORS=	python3
FLAVOR=		python3

.include <bsd.port.mk>

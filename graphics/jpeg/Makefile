COMMENT=	SIMD-accelerated JPEG codec replacement of libjpeg

V=		3.0.1
DISTNAME=	libjpeg-turbo-${V}
PKGNAME=	jpeg-${V}
EPOCH=		0

SHARED_LIBS+=	jpeg		70.2
SHARED_LIBS+=	turbojpeg	0.2

CATEGORIES=	graphics
DPB_PROPERTIES=	parallel

HOMEPAGE=	https://libjpeg-turbo.org/

# BSD-style
PERMIT_PACKAGE=	Yes

SITES=		${SITE_SOURCEFORGE:=libjpeg-turbo/}

WANTLIB=	c m

MODULES=	devel/cmake

.if ${MACHINE_ARCH} == "amd64" || ${MACHINE_ARCH} == "i386"
BUILD_DEPENDS=	devel/yasm
.endif

CONFIGURE_ARGS+= -DCMAKE_INSTALL_PREFIX="${PREFIX}"
DEBUG_PACKAGES=	${BUILD_PACKAGES}

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/jpeg
	${INSTALL_DATA} ${WRKSRC}/{libjpeg,wizard}.txt ${PREFIX}/share/doc/jpeg

.include <bsd.port.mk>

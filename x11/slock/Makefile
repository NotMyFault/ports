COMMENT=		simple X screen locker

DISTNAME=		slock-1.4

CATEGORIES=		x11

HOMEPAGE=		http://tools.suckless.org/slock

MAINTAINER=		Gleydson Soares <gsoares@openbsd.org>

# BSD
PERMIT_PACKAGE=	Yes

WANTLIB=		X11 c Xext Xrandr

SITES=			http://dl.suckless.org/tools/

MAKE_FLAGS=		CC="${CC}" \
			COMPATSRC= \
			COPTFLAGS="${CFLAGS}" \
			MANPREFIX=${PREFIX}/man \
			X11INC=${X11BASE}/include \
			X11LIB=${X11BASE}/lib

NO_TEST=		Yes

.include <bsd.port.mk>

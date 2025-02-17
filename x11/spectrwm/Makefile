COMMENT=		small tiling window manager

V=			3.5.0
DIST_TUPLE=		github conformal spectrwm SPECTRWM_${V:S/./_/g} /
DISTNAME=		spectrwm-${V}

SHARED_LIBS=		swmhack 1.0

CATEGORIES=		x11

MAINTAINER=		Gonzalo L. R. <gonzalo@openbsd.org>, \
			Bjorn Ketelaars <bket@openbsd.org>

# BSD
PERMIT_PACKAGE=	Yes

COMPILER=	base-clang ports-gcc
COMPILER_LANGS=	c

# uses pledge()
WANTLIB += X11 X11-xcb Xcursor Xft c fontconfig util xcb xcb-icccm
WANTLIB += xcb-keysyms xcb-randr xcb-util xcb-xinput xcb-xtest

RUN_DEPENDS=	x11/dmenu>=4.5

MAKE_FLAGS=	BINDIR="${TRUEPREFIX}/bin" \
		MANDIR="${TRUEPREFIX}/man/man" \
		SHLIB_MAJOR=${LIBswmhack_VERSION:R} \
		SHLIB_MINOR=${LIBswmhack_VERSION:E}

DEBUG_PACKAGES=	${BUILD_PACKAGES}

NO_TEST=	Yes

pre-configure:
	@${SUBST_CMD} ${WRKSRC}/spectrwm.{1,c}

post-install:
	ln -s ${TRUEPREFIX}/bin/spectrwm ${PREFIX}/bin/scrotwm
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/spectrwm
	${INSTALL_SCRIPT} ${WRKSRC}/baraction.sh ${PREFIX}/share/examples/spectrwm
	${INSTALL_SCRIPT} ${WRKSRC}/initscreen.sh ${PREFIX}/share/examples/spectrwm
	${INSTALL_SCRIPT} ${WRKSRC}/screenshot.sh ${PREFIX}/share/examples/spectrwm
	${INSTALL_DATA} ${WRKSRC}/spectrwm.conf ${PREFIX}/share/examples/spectrwm

.for i in es cz fr fr_ch se us
	${INSTALL_DATA} ${WRKSRC}/spectrwm_$i.conf ${PREFIX}/share/examples/spectrwm
.endfor

.include <bsd.port.mk>

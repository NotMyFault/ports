COMMENT =		Qt GUI Interface for FluidSynth

DISTNAME =		qsynth-0.6.3
REVISION =		0

CATEGORIES =		audio

HOMEPAGE =		https://qsynth.sourceforge.io

MAINTAINER=		Sebastian Reitenbach <sebastia@openbsd.org>

# GPLv2+
PERMIT_PACKAGE =	Yes

SITES =			${SITE_SOURCEFORGE:=qsynth/}

WANTLIB += ${COMPILER_LIBCXX} Qt5Core Qt5Gui Qt5Widgets c
WANTLIB += m fluidsynth GL Qt5Network curses readline

MODULES =		x11/qt5

LIB_DEPENDS +=		audio/fluidsynth

RUN_DEPENDS +=		devel/desktop-file-utils \
			x11/gtk+4,-guic

USE_GMAKE =		Yes
NO_TEST =		Yes

CONFIGURE_STYLE = 	gnu

CONFIGURE_ENV +=	CPPFLAGS="${CPPFLAGS} -I${LOCALBASE}/include" \
			LDFLAGS="${LDFLAGS} -L${LOCALBASE}/lib -L${X11BASE}/lib" \
			ac_cv_path_ac_qmake="${MODQT_QMAKE}"

.if ${MACHINE_ARCH} == "hppa"
WANTLIB +=		atomic
.endif

.include <bsd.port.mk>

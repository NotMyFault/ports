COMMENT =		minimal CGI library for web applications

DISTNAME =		kcgi-0.13.1
CATEGORIES =		www

MAINTAINER =		James Turner <james@calminferno.net>

HOMEPAGE =		https://kristaps.bsd.lv/kcgi/
SITES =			${HOMEPAGE}snapshots/
EXTRACT_SUFX =		.tgz

# ISC
PERMIT_PACKAGE =	Yes

# uses pledge()
WANTLIB += c

CONFIGURE_STYLE =	simple
MAKE_FLAGS =		PREFIX="${PREFIX}"

TEST_DEPENDS =		net/curl
TEST_TARGET =		regress

.include <bsd.port.mk>

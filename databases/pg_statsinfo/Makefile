COMMENT =	monitor PostgreSQL activity & statistics

DISTNAME =	pg_statsinfo-13.0
CATEGORIES =	databases
REVISION =	0

HOMEPAGE =	https://pgstatsinfo.sourceforge.net/

# GPLv2
PERMIT_PACKAGE =	Yes

SITES=		${SITE_SOURCEFORGE:=pgstatsinfo/}

USE_GMAKE =	Yes
MAKE_FLAGS =	USE_PGXS=1 CFLAGS="-DPG_USE_INLINE" LDFLAGS=-lkvm

BUILD_DEPENDS =	databases/postgresql,-server
LIB_DEPENDS =	databases/postgresql

WANTLIB += c kvm pq pthread

.include <bsd.port.mk>

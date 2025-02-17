COMMENT=	spell checker with multi-language support

DISTNAME=	aspell-0.60.8
DIST_SUBDIR=	aspell
CATEGORIES=	textproc

SHARED_LIBS +=  aspell               18.0     # .18.1
SHARED_LIBS +=  pspell               17.0     # .18.1

DIST_EN=	aspell6-en-2020.12.07-0

SITES=		${SITE_GNU:=aspell/}
SITES.en=	${SITE_GNU:=aspell/dict/en/}

DISTFILES.en= 	${DIST_EN}.tar.bz2

HOMEPAGE=	http://aspell.net/

# LGPLv2.1
PERMIT_PACKAGE=	Yes

WANTLIB += ${COMPILER_LIBCXX} c curses iconv intl m

COMPILER = base-clang ports-gcc base-gcc

# use ld.lld on mips64 to avoid ld.bfd ICE:
# /usr/bin/ld: BFD 2.17 internal error, aborting at /usr/src/gnu/usr.bin/binutils-2.17/bfd/elfxx-mips.c line 4797 in mips_elf_create_dynamic_relocation
.if ${MACHINE_ARCH} == "mips64" || ${MACHINE_ARCH} == "mips64el"
USE_LLD =	Yes
.endif

LIB_DEPENDS=		devel/gettext,-runtime

CONFIGURE_STYLE=	gnu

CONFIGURE_ENV=		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib"

CONFIGURE_ARGS+=	--enable-static \
			--enable-curses=ncursesw \
			--enable-dict-dir=${PREFIX}/share/aspell \
			--enable-docdir=${PREFIX}/share/doc/aspell

post-build:
	cd ${WRKDIR}/${DIST_EN} && \
		cp ${WRKSRC}/data/* . && \
		LD_LIBRARY_PATH=${WRKBUILD}/.libs ./configure --vars \
			ASPELL=${WRKBUILD}/aspell \
			ASPELL_FLAGS="--local-data-dir=${WRKDIR}/${DIST_EN}" \
			PREZIP=${WRKBUILD}/prezip-bin && \
		${SETENV} ${MAKE_ENV} ${MAKE_PROGRAM} ${MAKE_FLAGS} \
			LD_LIBRARY_PATH=${WRKBUILD}/.libs

post-install:
	cd ${WRKDIR}/${DIST_EN} && \
		${SETENV} ${MAKE_ENV} ${MAKE_PROGRAM} \
			dictdir=${PREFIX}/share/aspell \
			datadir=${PREFIX}/lib/aspell \
			${INSTALL_TARGET}

.include <bsd.port.mk>

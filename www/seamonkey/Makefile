BROKEN =		fail to build with lang/rust 1.73.0: error: unrecognized platform-specific intrinsic function
BROKEN-aarch64 =	third_party/rust/libc/src/lib.rs: error[E0412]: cannot find type 'c_long' in this scope

COMMENT-main =		Mozilla application suite
COMMENT-lightning =	Mozilla Seamonkey calendar extension
ONLY_FOR_ARCHS =	amd64 i386 aarch64

# version = (TB version - 3) / 100 + 2
MOZILLA_VERSION =	2.53.17.1
MOZILLA_PROJECT =	seamonkey
MOZILLA_CODENAME =	comm/suite

MULTI_PACKAGES =	-main -lightning
PKGNAME-main =		${PKGNAME}
PKGNAME-lightning =	lightning-seamonkey-5.8.17.1
EPOCH-lightning =	0

HOMEPAGE =	https://www.seamonkey-project.org/

SO_VERSION =	47.0
# NOTE: Must bump minor version if any shlib's are removed from the
# components dir to avoid pkg_add -r issues.

MOZILLA_LIBS = ldap60 ldif60 mozavcodec mozavutil mozgtk mozsqlite3 prldap60 suite xul lgpllibs

CATEGORIES=	www mail net news

# MPL
PERMIT_PACKAGE=	Yes

MODULES =	www/mozilla lang/python lang/clang
MODPY_RUNDEP =	No

COMPILER =		base-clang ports-clang
MODCLANG_ARCHS =	amd64 i386
MODCLANG_COMPILER_LINKS =	No

CONFIGURE_ARGS +=	--disable-gconf
NO_TEST=	Yes

CONFIGURE_STYLE =	simple
CONFIGURE_ARGS +=	--prefix=${PREFIX}

BUILD_DEPENDS +=	devel/cbindgen>=0.6.1

# lld blows when linking libxul; limit threads
.if ${MACHINE_ARCH:Mi386}
CONFIGURE_ENV +=	LDFLAGS="-Wl,--threads=2"
# make sure we dont look for libatomic from gcc-libs
CONFIGURE_ENV +=	ac_cv_needs_atomic=no
.endif

RUN_DEPENDS-lightning = STEM->=${MOZILLA_VERSION:S/b/beta/}:${BUILD_PKGPATH},-main
WANTLIB += Xt gthread-2.0 pangoft2-1.0

WANTLIB-lightning=

MAKE_ENV +=	RUSTC_BOOTSTRAP="packed_simd_2,encoding_rs"

# build lightning xpi
CONFIGURE_ARGS +=	--enable-calendar
# remove post 96
CONFIGURE_ARGS +=	--disable-necko-wifi

# XXX badly formed debug ?
DWZ = :
DEBUG_PACKAGES =	${BUILD_PACKAGES}
DEBUG_CONFIGURE_ARGS +=	--enable-debug-symbols \
			--disable-install-strip

post-install:
	${INSTALL_MAN} ${WRKBUILD}/dist/man/man1/seamonkey.1 ${PREFIX}/man/man1/

	# install prefs
	${SUBST_DATA} ${FILESDIR}/all-openbsd.js \
		${PREFIX}/lib/${MOZILLA_PROJECT}/defaults/pref/all-openbsd.js
	# install desktop file
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications/ ; \
	${INSTALL_DATA} ${FILESDIR}/${MOZILLA_PROJECT}.desktop \
		${PREFIX}/share/applications/${MOZILLA_PROJECT}.desktop ; \

	# install icons for desktop file
.for s in 16 22 24 32 48 64 128 256
	${INSTALL_DATA_DIR} ${PREFIX}/share/icons/hicolor/${s}x${s}/apps
	${INSTALL_DATA} ${WRKSRC}/comm/suite/branding/seamonkey/default${s}.png \
		${PREFIX}/share/icons/hicolor/${s}x${s}/apps/org.mozilla.${MOZILLA_PROJECT}.png
.endfor
	${INSTALL_DATA_DIR} ${PREFIX}/share/icons/hicolor/scalable/apps
	${INSTALL_DATA} ${FILESDIR}/org.mozilla.${MOZILLA_PROJECT}.svg ${PREFIX}/share/icons/hicolor/scalable/apps/org.mozilla.${MOZILLA_PROJECT}.svg

.include <bsd.port.mk>

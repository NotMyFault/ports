GH_ACCOUNT =	google
GH_PROJECT =	boringssl
GH_COMMIT =	ad57528d2c978543106f9b115bd0eb658f3ebdd2
DISTNAME =	boringssl-20231106

SITES.mods =	https://proxy.golang.org/

DISTFILES +=	${GH_DISTFILE}
# can't use GH_DISTFILE because EXTRACT_ONLY does not understand DISTFILES {}
EXTRACT_ONLY =	${ALL_DISTFILES:Mboringssl*}

BORING_GOMOD +=	golang.org/x/crypto	v0.14.0
BORING_GOMOD +=	golang.org/x/net	v0.17.0
BORING_GOMOD +=	golang.org/x/sys	v0.13.0
BORING_GOMOD +=	golang.org/x/term	v0.13.0

.for _modpath _modver in ${BORING_GOMOD}
DISTFILES.mods +=	go_modules/{}${_modpath}/@v/${_modver}.zip
DISTFILES.mods +=	go_modules/{}${_modpath}/@v/${_modver}.mod
.endfor

WANTLIB += ${COMPILER_LIBCXX} c m

# C++14
COMPILER =		base-clang ports-gcc

MODULES =		devel/cmake
CONFIGURE_ARGS +=	-DCMAKE_INSTALL_PREFIX=${PREFIX}/eboringssl

BUILD_DEPENDS =		lang/go

TEST_ENV =		GOPROXY=file://${DISTDIR}/go_modules

FIX_CLEANUP_PERMISSIONS =	Yes

do-test:
	${SETENV} ${ALL_TEST_ENV} ninja -C ${WRKBUILD} -j ${MAKE_JOBS} run_tests

.include <bsd.port.mk>

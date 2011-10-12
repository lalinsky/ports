# New ports collection makefile for:	chromaprint
# Date created:		29 December 2010
# Whom:			Andrew Pantyukhin <infofarmer@FreeBSD.org>
#
# $FreeBSD$
#

PORTNAME=	chromaprint
PORTVERSION=	0.5
CATEGORIES=	audio
MASTER_SITES=	https://github.com/lalinsky/${PORTNAME}/tarball/${COMMIT}/

MAINTAINER=	infofarmer@FreeBSD.org
COMMENT=	A chroma-based acoustic fingerprinter

LIB_DEPENDS=	avcodec.1:${PORTSDIR}/multimedia/ffmpeg \
		tag:${PORTSDIR}/audio/taglib \
		gtest:${PORTSDIR}/devel/googletest/ \
		boost_filesystem:${PORTSDIR}/devel/boost-libs

LICENSE=	LGPL21

FETCH_ARGS=	-Fpr
COMMIT=	f2c45fb
WRKSRC=	${WRKDIR}/lalinsky-${PORTNAME}-${COMMIT}
USE_LDCONFIG=	yes
USE_CMAKE=	yes
CMAKE_ARGS=	-Wno-dev -DCMAKE_EXE_LINKER_FLAGS:STRING="-L${LOCALBASE}/lib" \
		-DBUILD_TOOLS:BOOL=ON
CFLAGS+=	-I${LOCALBASE}/include
CMAKE_VERBOSE=	yes

PLIST_FILES=	bin/chroma-fpcollect bin/chroma-fpsubmit \
		lib/libchromaprint.so.0.1.2 lib/libchromaprint.so.0 \
		lib/libchromaprint.so include/chromaprint.h \
		libdata/pkgconfig/libchromaprint.pc

post-patch:
	@${REINPLACE_CMD} -e '/pc DESTINATION/s,$${LIB_INSTALL_DIR},$${CMAKE_INSTALL_PREFIX}/libdata,'\
		${WRKSRC}/CMakeLists.txt

post-install:
	@${INSTALL_PROGRAM} ${WRKSRC}/tools/fpcollect \
		${PREFIX}/bin/chroma-fpcollect
	@${INSTALL_SCRIPT} ${WRKSRC}/tools/fpsubmit.py \
		${PREFIX}/bin/chroma-fpsubmit

.include <bsd.port.mk>

# New ports collection makefile for:	chromaprint
# Date created:		29 December 2010
# Whom:			Andrew Pantyukhin <infofarmer@FreeBSD.org>
#
# $FreeBSD$
#

PORTNAME=	chromaprint
#PORTVERSION=	0.2.${REVNO}
PORTVERSION=	0.3
CATEGORIES=	audio
MASTER_SITES=	http://cloud.github.com/downloads/lalinsky/chromaprint/
#REVNO=		67

MAINTAINER=	infofarmer@FreeBSD.org
COMMENT=	A chroma-based acoustic fingerprinter

LIB_DEPENDS=	avcodec.1:${PORTSDIR}/multimedia/ffmpeg \
		tag:${PORTSDIR}/audio/taglib \
		boost_filesystem:${PORTSDIR}/devel/boost-libs

LICENSE=	LGPL21

#googletest

#USE_BZIP2=	yes
USE_LDCONFIG=	yes
USE_CMAKE=	yes
CMAKE_ARGS=	-Wno-dev -DCMAKE_EXE_LINKER_FLAGS:STRING="-L${LOCALBASE}/lib" \
		-DBUILD_TOOLS:BOOL=ON
CFLAGS+=	-I${LOCALBASE}/include
CMAKE_VERBOSE=	yes

PLIST_FILES=	bin/chroma-fpgen bin/chroma-fpcollect bin/chroma-fpsubmit \
		lib/libchromaprint.so.0.1.1 lib/libchromaprint.so.0 \
		lib/libchromaprint.so include/chromaprint.h \
		libdata/pkgconfig/libchromaprint.pc

post-patch:
	@${REINPLACE_CMD} -e '/pc DESTINATION/s,$${LIB_INSTALL_DIR},$${CMAKE_INSTALL_PREFIX}/libdata,'\
		${WRKSRC}/CMakeLists.txt

post-install:
	@${INSTALL_PROGRAM} ${WRKSRC}/tools/fpgen ${PREFIX}/bin/chroma-fpgen
	@${INSTALL_PROGRAM} ${WRKSRC}/tools/fpcollect \
		${PREFIX}/bin/chroma-fpcollect
	@${INSTALL_SCRIPT} ${WRKSRC}/tools/fpsubmit.py \
		${PREFIX}/bin/chroma-fpsubmit

dist:
	@bzr export -r ${REVNO} ${DISTFILES} lp:chromaprint

.include <bsd.port.mk>

# New ports collection makefile for:	py-chromaprint
# Date created:		2011-04-22
# Whom:			Lukas Lalinsky <lalinsky@gmail.com>
#
# $FreeBSD$
#

PORTNAME=	chromaprint
#PORTVERSION=	0.2.${REVNO}
PORTVERSION=	0.3
CATEGORIES=	devel python
MASTER_SITES=	http://cloud.github.com/downloads/lalinsky/chromaprint/
#REVNO=		67

PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	lalinsky@gmail.com
COMMENT=	Python bindings for chromaprint

LIB_DEPENDS=	chromaprint.0:${PORTSDIR}/audio/chromaprint

#USE_BZIP2=	yes
USE_PYTHON=	yes
USE_PYDISTUTILS=	yes

WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}/python
PYDISTUTILS_EGGINFO=    Chromaprint-0.3-py${PYTHON_VER}.egg-info

.include <bsd.port.mk>

# Created by: Edwin Groothuis <edwin@mavetju.org>
# $FreeBSD$

PORTNAME=	fpdns
PORTVERSION=	0.10.0.20190131
CATEGORIES=	dns net perl5

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Fingerprinting DNS servers

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	p5-Net-DNS>=0.42:dns/p5-Net-DNS
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

NO_ARCH=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	kirei
GH_TAGNAME=	${PORTVERSION:E}

.include <bsd.port.mk>

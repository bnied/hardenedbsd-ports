# Created by: Dennis Herrmann <adox@mcx2.org>
# $FreeBSD$

PORTNAME=	vnstat
PORTVERSION=	2.0
PORTREVISION=	2
CATEGORIES=	net
MASTER_SITES=	https://humdi.net/vnstat/ \
		https://source.ipfire.org/source-2.x/

MAINTAINER=	feld@FreeBSD.org
COMMENT=	Console-based network traffic monitor

LICENSE=	GPLv2

USE_RC_SUBR=	vnstat

LIB_DEPENDS=	libsqlite3.so:databases/sqlite3

CFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
GNU_CONFIGURE=	yes

USE_HARDENING=	cfi safestack

USES=	gmake
USERS=	vnstat
GROUPS=	vnstat

PORTDOCS=	README INSTALL_BSD UPGRADE
SUB_FILES=	pkg-message
SUB_LIST=	USERS=${USERS} \
		GROUPS=${GROUPS}

OPTIONS_DEFINE=	GUI DOCS
OPTIONS_DEFAULT=	GUI
OPTIONS_SUB=	yes
GUI_DESC=	Build with graphics/gd dependency

GUI_LIB_DEPENDS+=	libgd.so:graphics/gd

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/vnstat ${STAGEDIR}/${PREFIX}/bin/vnstat
	${INSTALL_PROGRAM} ${WRKSRC}/vnstatd ${STAGEDIR}/${PREFIX}/sbin/vnstatd
	${INSTALL_DATA} ${WRKSRC}/cfg/vnstat.conf ${STAGEDIR}/${PREFIX}/etc/vnstat.conf.sample
	${INSTALL_MAN} ${WRKSRC}/man/vnstat.1 ${STAGEDIR}/${MANPREFIX}/man/man1/vnstat.1
	${INSTALL_MAN} ${WRKSRC}/man/vnstatd.1 ${STAGEDIR}/${MANPREFIX}/man/man1/vnstatd.1
	${INSTALL_MAN} ${WRKSRC}/man/vnstat.conf.5 ${STAGEDIR}/${MANPREFIX}/man/man5/vnstat.conf.5

do-install-GUI-on:
	${INSTALL_PROGRAM} ${WRKSRC}/vnstati ${STAGEDIR}/${PREFIX}/bin/vnstati
	${INSTALL_MAN} ${WRKSRC}/man/vnstati.1 ${STAGEDIR}/${MANPREFIX}/man/man1/vnstati.1

post-install-DOCS-on:
	@${ECHO_MSG} "installing additional documentation to ${DOCSDIR}"
	@${MKDIR} ${STAGEDIR}/${DOCSDIR}
	@cd ${WRKSRC} && ${INSTALL_DATA} ${PORTDOCS} ${STAGEDIR}/${DOCSDIR}

.include <bsd.port.mk>

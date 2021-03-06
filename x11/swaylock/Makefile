# $FreeBSD$

PORTNAME=	swaylock
DISTVERSION=	1.2-46
DISTVERSIONSUFFIX=	-geffdea5
CATEGORIES=	x11

MAINTAINER=	jbeich@FreeBSD.org
COMMENT=	Screen locker for Wayland

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	wayland-protocols>=1.14:graphics/wayland-protocols
LIB_DEPENDS=	libwayland-client.so:graphics/wayland \
		libxkbcommon.so:x11/libxkbcommon

USES=		compiler:c11 meson pkgconfig
USE_GITHUB=	yes
GH_ACCOUNT=	swaywm
USE_GNOME=	cairo pango
MESON_ARGS=	-Dswaylock-version="${DISTVERSIONFULL}"
PLIST_FILES=	bin/${PORTNAME} \
		etc/pam.d/${PORTNAME} \
		share/bash-completion/completions/${PORTNAME} \
		share/fish/completions/${PORTNAME}.fish \
		share/zsh/site-functions/_${PORTNAME}

OPTIONS_DEFINE=	MANPAGES PIXBUF
OPTIONS_DEFAULT=MANPAGES PIXBUF

MANPAGES_BUILD_DEPENDS=	scdoc:textproc/scdoc
MANPAGES_MESON_ON=	-Dman-pages=enabled
MANPAGES_MESON_OFF=	-Dman-pages=disabled
MANPAGES_PLIST_FILES=	man/man1/${PORTNAME}.1.gz

PIXBUF_USE=		GNOME=gdkpixbuf2
PIXBUF_MESON_ON=	-Dgdk-pixbuf=enabled
PIXBUF_MESON_OFF=	-Dgdk-pixbuf=disabled

.include <bsd.port.mk>

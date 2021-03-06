#
# Copyright (C) 2008-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=cairo
PKG_VERSION:=1.16.0
PKG_RELEASE:=3

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://cairographics.org/releases/
PKG_MD5SUM:=f19e0353828269c22bd72e271243a552
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

define Package/cairo
  SECTION:=xorg-libraries
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=Multi-platform 2D graphics library
  DEPENDS:=+fontconfig +libpng +libexpat +pixman +liblzo \
  +@directfb \
  +libX11 +libXext +libXrender +libxcb +libxcb-shm +libxcb-render \
  +glib2
  URL:=http://cairographics.org/
endef

define Package/cairo/description
Cairo is a 2D graphics library. The cairo API provides operations similar
to the drawing operators of PostScript and PDF. Operations in cairo
include stroking and filling cubic Bézier splines, transforming and
compositing translucent images, and antialiased text rendering. All
drawing operations can be transformed by any affine transformation
(scale, rotation, shear, etc.).
endef

CONFIGURE_VARS+=FONTCONFIG_LIBS="-lfreetype -lfontconfig -lz -lexpat"

CONFIGURE_ARGS+= \
	--enable-freetype=yes \
	--disable-win32 \
	--enable-xlib-xrender=no

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig/
	$(INSTALL_DIR) $(1)/usr/include/cairo/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/include/cairo/* $(1)/usr/include/cairo/
endef

define Package/cairo/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,cairo))

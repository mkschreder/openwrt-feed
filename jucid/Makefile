include $(TOPDIR)/rules.mk

PKG_NAME:=jucid

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mkschreder/jucid.git
PKG_SOURCE_VERSION:=d8413909620c405b3c05b70277d19f07b249eb4d
PKG_VERSION:=$(PKG_SOURCE_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Martin K. Schröder <mkschreder.uk@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/jucid
  SECTION:=base
  CATEGORY:=Base system
  DEPENDS:=+libubus2 +liblua +ubus-json-server
  TITLE:=JUCI Backend Server
endef

define Package/jucid/configure
	./configure 
endef 

define Build/Configure
	$(call Build/Configure/Default)
endef

define Package/jucid/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/jucid $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/jucid.init $(1)/etc/init.d/juci
endef

$(eval $(call BuildPackage,jucid))

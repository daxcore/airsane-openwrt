include $(TOPDIR)/rules.mk

PKG_NAME:=airsaned
PKG_VERSION:=0.4.9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/SimulPiscator/AirSane/tar.gz/v$(PKG_VERSION)?
PKG_SOURCE_DATE:=2026-02-18
PKG_HASH:=b8be7057c20ad896b3303a2ac2fe481ccf73933a59b105724ca0467896853dde

PKG_MAINTAINER:=SimulPiscator <example@example.com>
PKG_LICENSE:=GPL-3.0

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

TAR_OPTIONS:=--strip-components 1 $(TAR_OPTIONS)
TAR_CMD=$(HOST_TAR) -C $(1) $(TAR_OPTIONS)

define Package/airsaned
  TITLE:=A SANE WebScan frontend that supports Apple's AirScan protocol
  URL:=https://github.com/SimulPiscator/AirSane
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libsane +libjpeg +libpng +libavahi-client +libusb-1.0 +libstdcpp +libatomic
endef

define Package/airsaned/description
  A SANE WebScan frontend that supports Apple's AirScan protocol
endef

define Package/airsaned/conffiles
	/etc/config/airsaned
endef

define Package/airsaned/install 
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/airsaned $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) files/airsaned.init $(1)/etc/init.d/airsaned
	$(INSTALL_DIR) $(1)/etc/config/
	$(CP) files/airsaned.default $(1)/etc/config/airsaned
endef

$(eval $(call BuildPackage,airsaned))

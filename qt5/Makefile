include $(TOPDIR)/rules.mk

PKG_NAME:=qt5
PKG_BASE:=5.15
PKG_BUGFIX:=2
PKG_VERSION:=$(PKG_BASE).$(PKG_BUGFIX)
PKG_RELEASE:=1

PKG_SOURCE:=qt-everywhere-src-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://download.qt.io/archive/qt/5.15/$(PKG_VERSION)/single
PKG_HASH:=3a530d1b243b5dec00bc54937455471aaa3e56849d2593edb8ded07228202240

PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

PKG_BUILD_DIR=$(BUILD_DIR)/qt-everywhere-src-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

ifndef CONFIG_USE_GLIBC
# not using sstrip here as this screw up the .so's somehow
STRIP:=/bin/true
RSTRIP:= \
	NM="$(TOOLCHAIN_DIR)/bin/$(TARGET_CROSS)nm" \
	STRIP="$(STRIP)" \
	STRIP_KMOD="$(STRIP)" \
	$(SCRIPT_DIR)/rstrip.sh
endif

define Package/qt5/Default
	SECTION:=libs
	CATEGORY:=Libraries
	SUBMENU:=Qt5
	TITLE:=qt5
	URL:=http://qt-project.org
	DEPENDS:=+librt +libstdcpp +libpthread +zlib @!LINUX_2_6_36
endef

define Package/qt5-core
	$(call Package/qt5/Default)
	TITLE+=core
	DEPENDS+=+libatomic
endef

define Package/qt5-network
	$(call Package/qt5/Default)
	TITLE+=network
	DEPENDS+=+qt5-core +libopenssl
endef

define Package/qt5-xml
	$(call Package/qt5/Default)
	TITLE+=xml
	DEPENDS+=+qt5-core
endef

define Build/Configure
	$(INSTALL_DIR) $(PKG_BUILD_DIR)/qtbase/mkspecs/linux-openwrt-g++
	$(CP) ./files/qplatformdefs.h $(PKG_BUILD_DIR)/qtbase/mkspecs/linux-openwrt-g++/qplatformdefs.h
	$(CP) ./files/qmake.conf $(PKG_BUILD_DIR)/qtbase/mkspecs/linux-openwrt-g++/qmake.conf
	$(SED) 's@$$$$(TARGET_CROSS)@$(TARGET_CROSS)@g' $(PKG_BUILD_DIR)/qtbase/mkspecs/linux-openwrt-g++/qmake.conf
	( cd $(PKG_BUILD_DIR) ; \
		./configure \
			-prefix /usr \
			-I $(STAGING_DIR)/usr/include \
			-extprefix $(TOOLCHAIN_DIR) \
			-sysroot $(TOOLCHAIN_DIR) \
			-plugindir /usr/lib/Qt/plugins \
			-xplatform linux-openwrt-g++ \
			-opensource \
			-confirm-license \
			-release \
			-openssl-linked \
			-qt-doubleconversion \
			-system-zlib \
			-no-angle \
			-no-compile-examples \
			-no-cups \
			-no-dbus \
			-no-directfb \
			-no-dtls\
			-no-egl \
			-no-eglfs \
			-no-feature-getentropy \
			-no-feature-concurrent \
			-no-feature-gssapi \
			-no-feature-sql \
			-no-feature-testlib \
			-no-freetype \
			-no-gbm \
			-no-glib \
			-no-gtk \
			-no-gui \
			-no-harfbuzz \
			-no-iconv \
			-no-icu \
			-no-kms \
			-no-libjpeg \
			-no-libmd4c \
			-no-libpng \
			-no-libudev \
			-no-mtdev \
			-no-opengl \
			-no-openvg \
			-no-opengles3 \
			-no-pch \
			-no-rpath \
			-no-slog2 \
			-no-sql-db2 \
			-no-sql-ibase \
			-no-sql-mysql \
			-no-sql-oci \
			-no-sql-odbc \
			-no-sql-psql \
			-no-sql-sqlite \
			-no-sql-sqlite2 \
			-no-sql-tds \
			-no-sqlite \
			-no-strip \
			-no-trace \
			-no-tslib \
			-no-vulkan \
			-no-xcb \
			-no-xkbcommon \
			-no-widgets \
			-no-zstd \
			-make libs \
			-nomake examples \
			-nomake tests \
			-nomake tools \
			-skip 3d \
			-skip activeqt \
			-skip androidextras \
			-skip canvas3d \
			-skip charts \
			-skip connectivity \
			-skip datavis3d \
			-skip declarative \
			-skip doc \
			-skip gamepad \
			-skip graphicaleffects \
			-skip imageformats \
			-skip location \
			-skip lottie \
			-skip macextras \
			-skip multimedia \
			-skip networkauth \
			-skip purchasing \
			-skip quick3d \
			-skip quickcontrols \
			-skip quickcontrols2 \
			-skip quicktimeline \
			-skip remoteobjects \
			-skip script \
			-skip scxml \
			-skip sensors \
			-skip serialbus \
			-skip serialport \
			-skip speech \
			-skip svg \
			-skip translations \
			-skip virtualkeyboard \
			-skip wayland \
			-skip webchannel \
			-skip webengine \
			-skip webglplugin \
			-skip websockets \
			-skip winextras \
			-skip webview \
			-skip x11extras \
			-skip xmlpatterns \
			-v \
	)
endef

define Build/Compile
	$(MAKE) -j4 -C $(PKG_BUILD_DIR)
endef

define Build/InstallDev
	$(MAKE) -C $(PKG_BUILD_DIR) install
	$(CP) $(PKG_BUILD_DIR)/qtbase/bin/qt.conf $(TOOLCHAIN_DIR)/bin
	$(RM) $(TOOLCHAIN_DIR)/bin/qt{diag,paths,plugininfo}
endef

define Package/qt5-core/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Core.so* $(1)/usr/lib
endef

define Package/qt5-network/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Network.so* $(1)/usr/lib
endef

define Package/qt5-xml/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/qtbase/lib/libQt5Xml.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,qt5-core))
$(eval $(call BuildPackage,qt5-network))
$(eval $(call BuildPackage,qt5-xml))

#
# Copyright (C) 2007-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12271 2008-08-10 16:12:31Z nbd $

include $(TOPDIR)/rules.mk

PKG_NAME:=egenix-mx
PKG_VERSION:=2.0.6
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-base-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://downloads.egenix.com/python/
PKG_MD5SUM:=66841151728a06f92d0b8dd2ed317a29

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-base-$(PKG_VERSION)
PKG_BUILD_DEPENDS:=python

include $(INCLUDE_DIR)/package.mk
-include $(if $(DUMP),,$(STAGING_DIR)/mk/python-package.mk)

define Package/python-egenix-mx
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  DEPENDS:=python-core
  TITLE:=Egenix mxBase
  URL:=http://www.egenix.com/products/python/mxBase/
endef

define Package/python-egenix-mx/description
 This package contains a set of base packages from Egenix required by other 
 python packages.
endef

define Build/Compile
	$(if $(Build/Compile/PyMod),,@echo Python packaging code not found.; false)
	$(call Build/Compile/PyMod,., \
		build --build-lib="foo", \
		BASECFLAGS="$(TARGET_CFLAGS)" \
		OPT="" \
	)
endef

define Build/InstallDev
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/BeeBase/mxBeeBase
	$(CP) \
		$(PKG_BUILD_DIR)/mx/BeeBase/mxBeeBase/mxh.h \
		$(PKG_BUILD_DIR)/mx/BeeBase/mxBeeBase/btr.h \
		$(PKG_BUILD_DIR)/mx/BeeBase/mxBeeBase/mxBeeBase.h \
		$(1)$(PYTHON_PKG_DIR)/mx/BeeBase/mxBeeBase/
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/DateTime/mxDateTime
	$(CP) \
		$(PKG_BUILD_DIR)/mx/DateTime/mxDateTime/mxh.h \
		$(PKG_BUILD_DIR)/mx/DateTime/mxDateTime/mxDateTime.h \
		$(1)$(PYTHON_PKG_DIR)/mx/DateTime/mxDateTime/
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/Proxy/mxProxy
	$(CP) \
		$(PKG_BUILD_DIR)/mx/Proxy/mxProxy/mxh.h \
		$(PKG_BUILD_DIR)/mx/Proxy/mxProxy/mxProxy.h \
		$(1)$(PYTHON_PKG_DIR)/mx/Proxy/mxProxy/
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/Queue/mxQueue
	$(CP) \
		$(PKG_BUILD_DIR)/mx/Queue/mxQueue/mxh.h \
		$(PKG_BUILD_DIR)/mx/Queue/mxQueue/mxQueue.h \
		$(1)$(PYTHON_PKG_DIR)/mx/Queue/mxQueue/
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/TextTools/mxTextTools
	$(CP) \
		$(PKG_BUILD_DIR)/mx/TextTools/mxTextTools/mxh.h \
		$(PKG_BUILD_DIR)/mx/TextTools/mxTextTools/mxbmse.h \
		$(PKG_BUILD_DIR)/mx/TextTools/mxTextTools/mxte.h \
		$(PKG_BUILD_DIR)/mx/TextTools/mxTextTools/mxTextTools.h \
		$(1)$(PYTHON_PKG_DIR)/mx/TextTools/mxTextTools/
	mkdir -p $(1)$(PYTHON_PKG_DIR)/mx/Tools/mxTools
	$(CP) \
		$(PKG_BUILD_DIR)/mx/Tools/mxTools/mxh.h \
		$(PKG_BUILD_DIR)/mx/Tools/mxTools/mxTools.h \
		$(1)$(PYTHON_PKG_DIR)/mx/Tools/mxTools/
endef

define PyPackage/python-egenix-mx/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) $(PKG_BUILD_DIR)/foo/mx $(1)$(PYTHON_PKG_DIR)/
	ln -sf	$(1)$(PYTHON_PKG_DIR)/mx/BeeBase/ExitFunctions.py \
		$(1)$(PYTHON_PKG_DIR)/mx/Misc/
	rm -rf	$(1)$(PYTHON_PKG_DIR)/mx/*/Examples
endef

$(eval $(call PyPackage,python-egenix-mx))
$(eval $(call BuildPackage,python-egenix-mx))

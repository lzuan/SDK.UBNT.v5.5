#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12175 2008-08-05 22:04:10Z florian $

include $(TOPDIR)/rules.mk

PKG_NAME:=nfs-server
PKG_VERSION:=2.2beta47
PKG_RELEASE:=1
PKG_MD5SUM:=79a29fe9f79b2f3241d4915767b8c511

PKG_SOURCE_URL:=http://ftp.debian.org/debian/pool/main/n/nfs-user-server
PKG_SOURCE:=nfs-user-server_$(PKG_VERSION).orig.tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/nfs-server
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+portmap
  TITLE:=User Space NFS server
endef

define Package/nfs-server/description
User Space NFS server
endef

define Build/Compile	
	$(MAKE) -C $(PKG_BUILD_DIR)
endef

define Package/nfs-server/install	
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) ./files/nfsd.exports $(1)/etc/exports
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/nfsd.init $(1)/etc/init.d/nfsd
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/rpc.* $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,nfs-server))

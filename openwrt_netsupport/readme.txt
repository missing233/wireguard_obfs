modify_file:   openwrt/package/kernel/linux/modules/netsupport.mk


define KernelPackage/wireguard_obf
  SUBMENU:=$(NETWORK_SUPPORT_MENU)
  TITLE:=WireGuard Obfuscated secure network tunnel
  DEPENDS:= \
	  +kmod-crypto-lib-chacha20poly1305 \
	  +kmod-crypto-lib-curve25519 \
	  +kmod-udptunnel4 \
	  +IPV6:kmod-udptunnel6
  KCONFIG:= \
	  CONFIG_WIREGUARD_OBF \
	  CONFIG_WIREGUARD_OBF_DEBUG=n
  FILES:=$(LINUX_DIR)/drivers/net/wireguard_obf/wireguard_obf.ko
  AUTOLOAD:=$(call AutoProbe,wireguard_obf)
endef

define KernelPackage/wireguard_obf/description
  WireGuard Obfuscated is a novel VPN that runs inside the Linux Kernel and utilizes
  state-of-the-art cryptography. It aims to be faster, simpler, leaner, and
  more useful than IPSec, while avoiding the massive headache. It intends to
  be considerably more performant than OpenVPN.  WireGuard is designed as a
  general purpose VPN for running on embedded interfaces and super computers
  alike, fit for many different circumstances. It uses UDP.
endef

$(eval $(call KernelPackage,wireguard_obf))

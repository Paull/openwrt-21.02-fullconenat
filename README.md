## Netfilter and iptables extension for [FULLCONENAT](https://github.com/Chion82/netfilter-full-cone-nat) target ported to OpenWrt 21.02.

Compile
---
```
# cd to OpenWrt source path

# Download kernel patch to target/linux/generic/hack-5.4/
wget -P target/linux/generic/hack-5.4/ https://github.com/Paull/openwrt-fullconenat/raw/master/files/952-net-conntrack-events-support-multiple-registrant.patch

# Download firewall3 patch to package/network/config/firewall/patches/
mkdir package/network/config/firewall/patches
wget -P package/network/config/firewall/patches/ https://github.com/Paull/openwrt-fullconenat/raw/master/files/fullconenat-fw3.patch

# Clone this repo
git clone -b master --single-branch https://github.com/Paull/openwrt-fullconenat package/fullconenat

# Select Network -> Firewall -> iptables-mod-fullconenat
make menuconfig

# Compile
make V=s
```

References
---
- fullconenat module for iptables is from [Chion82](https://github.com/Chion82/netfilter-full-cone-nat), I'v tested and it's compatible from kernel 4.14 to 5.4
- firewall3 patch for kernel 5.4 is modified from [LGA1150's patch](https://github.com/LGA1150/fullconenat-fw3-patch)
- kernel patch for kernel 5.4 is from [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede/blob/master/target/linux/generic/hack-5.4/952-net-conntrack-events-support-multiple-registrant.patch)

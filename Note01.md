#### `VMware`配置`Nvidia`显卡

虚拟机设置

```shell
hypervisor.cpuid.v0 FALSE
pciPassthru.64bitMMIOSizeGB 64
pciPassthru.use64bitMMIO TRUE
lsmod | grep nouveau

vim /etc/modprobe.d/blacklist.conf
# 添加
blacklist nouveau
options nouveau modeset=0

# 重新生成初始化RAM磁盘
sudo dracut --force # Fedora、CentOS

update-initramfs -u #Ubuntu、Debian

# 重启
reboot

ubuntu-drivers devices
```
---
title: 'Ubuntu rootfs for aarch64 on x86 Host
'
date: 2021-01-29
permalink: /posts/2021/01/aarch64-rootfs/
tags:
  - cool posts
  - category1
  - category2
---

# This post will introduce how to prepare Ubuntu rootfs for aarch64 on x86 Host

## 1. Install pre-required packages on x86 host

sudo apt install qemu qemu-user-static binfmt-support debootstrap

## 2. Download Ubuntu base rootfs and uncompress to a folder

wget http://cdimage.ubuntu.com/ubuntu-base/releases/20.04/release/ubuntu-base-20.04.1-base-arm64.tar.gz

tar -xzvf ubuntu-base-20.04.1-base-arm64.tar.gz tmp

## 3. Prepare network configuration

sudo cp -b /etc/resolv.conf tmp/etc/resolv.conf

## 4. Prepare qemu

sudo cp /usr/bin/qemu-aarch64-static tmp/usr/bin/

## 5. Set new root folder

sudo chroot tmp

## 6. Update and upgrade packages

apt update && apt upgrade -y

## 7. Install necessary packages

apt install sudo ifupdown net-tools network-manager udev sudo ssh vim resolvconf

## 8. Add user and password

useradd -s '/bin/bash' -m -G adm,sudo udrc

passwd udrc

passwd root

## 9. (Optional) Static IP addres

Answer 'no' to 'sudo dpkg-reconfigure resolvconf'. This is to set static configuration for /etc/resolv.conf file.

echo 'nameserver 10.42.0.1' > /etc/resolv.conf

echo 'eth0' > /etc/network/interfaces.d/eth0

echo 'iface eth0 net static' >> /etc/network/interfaces.d/eth0

echo 'address 10.42.0.106' >> /etc/network/interfaces.d/eth0

echo 'netmask 255.255.255.0' >> /etc/network/interfaces.d/eth0

echo 'gateway 10.42.0.1' >> /etc/network/interfaces.d/eth0

echo 'dns-nameservers 10.42.0.1' >> /etc/network/interfaces.d/eth0

## 10. Exit the new rootfs system

exit

## 11. (Optional) Make rootfs image

dd if=/dev/zero of=ubuntu_20.4_rootfs.img bs=1M count=2048

sudo mkfs.ext4 ubuntu_20.4_rootfs.img

mkdir rootfs

sudo mount ubuntu_20.4_rootfs.img rootfs/

sudo cp -rfp tmp/*  rootfs/

sudo umount rootfs/

e2fsck -p -f ubuntu_20.4_rootfs.img

resize2fs -M ubuntu_20.4_rootfs.img


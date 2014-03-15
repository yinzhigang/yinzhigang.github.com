---
layout: post
title: "OpenStack安装笔记"
date: 2013-09-26 15:04
comments: true
categories: OpenStack
---

折腾一个礼拜，终于算把OpenStack搭起来了。

教程：https://github.com/ist0ne/OpenStack-Grizzly-Install-Guide-CN/blob/OVS_Quantum_MutliNode/OpenStack_Grizzly_Install_Guide.rst

安装OpenVSwitch时遇到了点问题，模块编译通不过，后来发现Ubuntu内核版本为3.8，应该是OpenVSwitch还不支持，改用3.2版内核后成功安装。

虚拟机默认CPU是QEMU的虚拟CPU，性能极差，修改 /etc/nova/nova.conf，增加 libvirt_cpu_mode = host-passthrough 可直接使用物理机CPU，达到最大性能。但注意，只有KVM支持host-passthrough。详细说明：https://wiki.openstack.org/wiki/LibvirtXMLCPUModel

几个有用的资源：

陈沙克日志：http://www.chenshake.com/  国内OpenStack大牛

puppet-openstack: https://github.com/stackforge/puppet-openstack Puppet部署模块，正式环境大规模部署我计划用这个

Ubuntu OpenStack包地址: http://ubuntu-cloud.archive.canonical.com/ubuntu/dists/precise-updates/ 包括最新的Havana测试版也在，回头试试。

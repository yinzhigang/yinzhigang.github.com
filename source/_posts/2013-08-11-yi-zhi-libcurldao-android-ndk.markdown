---
layout: post
title: "移植libcurl到Android NDK"
date: 2013-08-11 17:50
comments: true
categories: [Android, NDK]
---

测试通过环境：
    操作系统：Mac OS
    NDK：NDK r8e
    libcurl：7.31.0

下载NDK环境: http://developer.android.com/tools/sdk/ndk/index.html ，安装环境不废话了。

在NDK安装目录执行
    ./build/tools/make-standalone-toolchain.sh
导出编译工具，一般生成压缩如 /tmp/ndk-zhigang/arm-linux-androideabi-4.6.tar.bz2。

解压：
    cd /opt/
    sudo tar xf /tmp/ndk-zhigang/arm-linux-androideabi-4.6.tar.bz2

下载curl源代码：http://curl.haxx.se/download.html

设置编译环境：
    export LDFLAGS="\
    -L/usr/local/Cellar/android-ndk/r8e/platforms/android-14/arch-arm/usr/lib"

    export CPPFLAGS="\
    -I/usr/local/Cellar/android-ndk/r8e/platforms/android-14/arch-arm/usr/include"

将以上路径修改为自己的NDK安装目录。

进入curl目录：
    ./configure --host=arm-linux-androideabi \
    --disable-ftp \
    --disable-gopher \
    --disable-file \
    --disable-imap \
    --disable-ldap \
    --disable-ldaps \
    --disable-pop3 \
    --disable-proxy \
    --disable-rtsp \
    --disable-smtp \
    --disable-telnet \
    --disable-tftp \
    --without-gnutls \
    --without-libidn \
    --without-librtmp \
    --without-ssl \
    --disable-dict

    mark

生成的静态库文件位于：lib/.libs/libcurl.a 动态库：libcurl.so.5.3.0

一般我们使用静态库文件。

复制 libcurl.a 到项目 jni/ 目录，修改 Android.mk 文件：

    # A simple test for the minimal standard C++ library
#

    LOCAL_PATH := $(call my-dir)

    include $(CLEAR_VARS)
    LOCAL_MODULE := curl
    LOCAL_SRC_FILES := libcurl.a
    include $(PREBUILT_STATIC_LIBRARY)

    include $(CLEAR_VARS)
    LOCAL_CFLAGS = -Wno-psabi
    LOCAL_MODULE := curltest
    LOCAL_SRC_FILES := curltest.c
    LOCAL_STATIC_LIBRARIES := libcurl
    LOCAL_C_INCLUDES += $(LOCAL_PATH)/include
    LOCAL_LDLIBS    += -lz

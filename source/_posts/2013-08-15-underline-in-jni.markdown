---
layout: post
title: "JAVA+jni 包名或方法名中含有下划线(_)的解决方法"
date: 2013-08-15 22:09
comments: true
categories: [Java, NDK, Android]
---

jni或NDK定义C函数是用下划线(\_)作为命名分隔。但如果JAVA包名或方法名里包含了\_ 那么就会发生找不到函数的错误，对此网上的各教程都说不要使用 \_，对于新项目，这种情况当然很容易避免，但若对一原有项目开发jni接口就麻烦了，特别是在 Android 平台下，包名决定着应用的唯一识别，轻易改不的。

经过不懈的努力，我终于找到了解决方法，简单来说就是在 \_ 后加1，如：

    // JAVA
    package net.zhigang.ndk_test;

    public class NdkTest
    {
        static {
            System.loadLibrary(ndktest);
        }
        public native void sayHello();
    }

    //C
    \#include <jni.h>

    jstring Java_net_zhigang_ndk_1test(JNIEnv* env, jobject thiz)
    {
        return env->NewStringUTF("Hello from jni");
    }

注意上面C语言部分的 ndk\_1test。

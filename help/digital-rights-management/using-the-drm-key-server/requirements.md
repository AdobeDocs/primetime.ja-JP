---
title: Primetime DRM キーサーバーの使用の要件
description: Primetime DRM キーサーバーの使用の要件
copied-description: true
exl-id: a5c0db05-15a1-45b0-abb9-11f857f5e34c
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# はじめに {#introduction}

Primetime DRM キーサーバーは、リモートiOSや Xbox 360 のキー配信用のマルチテナントキーサーバーです。 iOSのポリシーでリモートキー配信が有効になっている場合、iOSクライアントでのコンテンツ再生を有効にするには、Primetime DRM キーサーバーをデプロイする必要があります。 Xbox 360 では、Primetime DRM キーサーバーが常に必要です。

## Primetime DRM キーサーバーの使用の要件 {#requirements-for-using-primetime-drm-key-server}

Primetime DRM キーサーバーを使用する際の最小要件は次のとおりです。

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) または後で。 （Windows 64 ビットで HSM を使用するには、JRE 8 が必要です）

  >[!NOTE]
  >
  >64 ビット PKCS11 が OpenJDK 8 でサポートされるようになりました。 [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)、およびOracle
* [Apache Tomcat 7](https://tomcat.apache.org)
* Adobeが発行した資格情報
* Microsoftが発行した資格情報（Xbox 360 クライアントの場合）

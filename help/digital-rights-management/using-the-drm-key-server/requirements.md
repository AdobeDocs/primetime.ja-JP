---
title: Primetime DRM キーサーバーの使用の要件
description: Primetime DRM キーサーバーの使用の要件
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# はじめに {#introduction}

Primetime DRM キーサーバーは、リモートiOSや Xbox 360 のキー配信用のマルチテナントキーサーバーです。 iOSのポリシーでリモートキー配信が有効になっている場合、iOSクライアントでのコンテンツ再生を有効にするには、Primetime DRM キーサーバーをデプロイする必要があります。 Xbox 360 では、Primetime DRM キーサーバーが常に必要です。

## Primetime DRM キーサーバーの使用の要件 {#requirements-for-using-primetime-drm-key-server}

Primetime DRM キーサーバーを使用する場合の最小要件は次のとおりです。

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) または後で。 （Windows 64 ビットで HSM を使用するには、JRE 8 が必要です）

  >[!NOTE]
  >
  >64 ビット PKCS11 が OpenJDK 8 でサポートされるようになりました。 [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)、およびOracle
* [Apache Tomcat 7](https://tomcat.apache.org)
* Adobeが発行した資格情報
* Microsoftが発行した資格情報（Xbox 360 クライアントの場合）

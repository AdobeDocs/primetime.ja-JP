---
seo-title: Primetime DRMキーサーバーの使用に関する要件
title: Primetime DRMキーサーバーの使用に関する要件
uuid: 769f9e10-7a3e-4a38-b30d-18181b666bb4
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# はじめに{#introduction}

Primetime DRM Key Serverは、リモートiOSやXbox 360キー配信用のマルチテナントキーサーバーです。 iOSのポリシーでリモートキー配信が有効になっている場合、iOSクライアントでコンテンツの再生を有効にするには、Primetime DRMキーサーバーを展開する必要があります。 Xbox 360にはPrimetime DRMキーサーバーが必要です。

## Primetime DRMキーサーバー{#requirements-for-using-primetime-drm-key-server}の使用に関する要件

Primetime DRMキーサーバーを使用するための最小要件は次のとおりです。

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 以降。（Windows 64ビットでHSMを使用するには、JRE 8が必要）

   >[!NOTE]
   >
   >64ビットPKCS11がOpenJDK 8でサポートされるようになりました。[https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)、OracleJDK:[https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559).

* [Apache Tomcat 7](https://tomcat.apache.org)
* Adobeが発行した資格情報
* Microsoftが発行した資格情報（Xbox 360クライアント用）
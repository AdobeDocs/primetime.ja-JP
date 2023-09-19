---
title: Primetime Offline Packager 2.x リリース
description: Primetime Offline Packager 2.1 および 2.3.1 リリースの新機能
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Primetime Offline Packager リリース {#primetime-offline-packager-x-releases}

Primetime Offline Packager 2.1 および 2.3.1 リリースの新機能

## Primetime Offline Packager 2.3.1（2016 年 10 月）の新機能  {#what-s-new-in-primetime-offline-packager-oct}

このリリースでは、MPEG-DASH の On-Demand プロファイルが有効になり、 `validate` PlaylistCreator ツール用のオプションと、以下に示す Multi-DRM シナリオに関する主な修正点がいくつかあります。

| **問題番号** | **説明** |
|---|---|
| PTPUB-985 | HLS AAXS と Sample-AES は、packager で生成されたキーに対しては機能しません。 |
| PTPUB-973 | 一部の特定の Widevine コンテンツの暗号化アルゴリズムのエラーを修正しました。 |
| PTPUB-964 | 特定のプレーヤー (Android TVSDK) の特定のメディアタイプに対して、CENC 暗号化が壊れました。 |
| PTPUB-954 | Sample-AES 暗号化は、デフォルトでは AAXS DRM をバイパスし、リモートキー配信が有効になっている場合にエラーが発生します。 |
| PTPUB-951 | Widevine で key_file_path が指定されていない場合、オフラインパッケージャは例外をスローしません。 代わりに NPE をスローします。 |

Primetime Packager の最新ドキュメントについては、 [https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

### バージョン 2.3.1 の既知の問題 {#known-issue-in-version}

このリリースには次の問題が存在します。

| **問題番号** | **説明** |
|---|---|
| PTPUB-1005 | AAXS DRM 用に生成された最終セットレベルの.mpd ファイルで、PlaylistCreatorが.pssh ファイルの正しい URL を提供しません。 |
| PTPUB-1001 | in_path パラメーターで空のパスが指定された場合、PlaylistCreator はエラーをスローする必要があります |
| PTPUB-990 | DASH の場合、Offline Packager は、パラメーターが `log_vi` &amp; `iv_out_path` が指定されている。 |
| PTPUB-980 | 設定ファイルをパッケージ化に使用する場合は、パラメーター `key_url` では、指定された入力から引用符は削除されません。 |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### 最小必要システム構成 {#minimum-system-requirements}

サポートされるオペレーティングシステム

* Linux CentOS 6.3 64 ビット

ハードウェア要件

* 3.2GHz Intel® Pentium® 4 プロセッサー ( デュアル Intel Xeon®以上を推奨 )

* 64 ビットオペレーティングシステム： 4GB の RAM（8GB を推奨）

* ハードディスク

(Disk-SAS)：最低 10GB (7,500 RPM)

(Disk-SSD)：読み取り/書き込み速度 400MBps

(NAS): 1 GB の専用リンク

ソフトウェア要件

* OracleJava SE 1.8 以降

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Java SE ソフトウェアを [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
1. という名前のAdobe Primetime Offline Packager 2.3.1 アーカイブファイルを抽出します。 `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` をディスクに追加します。

### Offline Packager 2.3.1 の設定 {#configuring-the-offline-packager}

設定手順については、Primetime Offline Packager の概要ガイド ( ) を参照してください。 [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Primetime Offline Packager 2.1（2015 年 7 月）の新機能 {#what-s-new-in-primetime-offline-packager-july}

PlayReady BuyDRM のサポート（DASH 用）。 詳しくは、ヘルプドキュメントを参照してください。 [こちらから入手可能](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

オフラインパッケージャに対しても、次の機能強化がおこなわれました。

PTPUB-780 EXT-X-START タグのサポートを追加

## Primetime Offline Packager 2.0（2015 年 6 月）の新機能 {#what-s-new-in-primetime-offline-packager-june}

DASH 出力のクリアのサポートが追加されました。 製品ドキュメントを参照してください。 [ここ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) 」を参照してください。

このリリースでは、次の問題も修正されました。

* PTPUB-783 Offline Packager で、空の WebVTT ファイルを処理できるようになりました。
* PTPUB- 781 特定のトランスコードされた MP4 アセットがオフラインパッケージャと共にパッケージ化され、MBR 出力が生成されるときの、Chrome での HLS 出力のアーティファクト。

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### 最小必要システム構成 {#minimum-system-requirements-1}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64 ビット

**ハードウェア要件**

* 3.2GHz Intel® Pentium® 4 プロセッサー ( デュアル Intel Xeon®以上を推奨 )

* 64 ビットオペレーティングシステム： 4GB の RAM（8GB を推奨）

* 1 Gb イーサネットカードを推奨（複数のネットワークカードと 10 Gb もサポート）

* ハードディスク

   * (Disk-SAS)：最低 10GB (7,500 RPM)
   * (Disk-SSD)：読み取り/書き込み速度 400MBps
   * (NAS): 1 GB の専用リンク

**ソフトウェア要件**

* OracleJava SE 1.8 以降

### Offline Packager 2.1 のインストール {#installing-offline-packager}

1. Java SE ソフトウェアを [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
1. を抽出します。 `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`をディスクに追加します。

### Offline Packager 2.1 の設定 {#configuring-the-offline-packager-1}

設定の詳細については、 Primetime Offline Packager はじめにを参照してください。 [https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。

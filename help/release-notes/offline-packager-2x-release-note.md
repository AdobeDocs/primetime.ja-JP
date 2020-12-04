---
title: Primetime Offline Packager 2.xのリリース
seo-title: Primetime Offline Packager 2.xのリリース
description: Primetime Offline Packager 2.1および2.3.1リリースの新機能
seo-description: Primetime Offline Packager 2.1および2.3.1リリースの新機能
uuid: 01926a10-890d-477d-b832-e22847d957e0
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 933a0711-846a-4bb7-bf51-b300822a93d4
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Primetime Offline Packagerのリリース{#primetime-offline-packager-x-releases}

Primetime Offline Packager 2.1および2.3.1リリースの新機能

## Primetime Offline Packager 2.3.1（2016年10月）の新機能{#what-s-new-in-primetime-offline-packager-oct}

このリリースでは、MPEG-DASHのオンデマンドプロファイルが有効になり、PlaylistCreatorツールの`validate`オプションのサポートが追加されます。また、以下に示すMulti-DRMシナリオに関する主な修正はいくつかあります。

| **問題番号** | **説明** |
|---|---|
| PTPUB-985 | HLS AAXSとSample-AESは、Packagerで生成されたキーに対しては機能しません。 |
| PTPUB-973 | 特定のWidevineコンテンツの暗号化アルゴリズムで発生していたエラーを修正しました。 |
| PTPUB-964 | 特定のプレーヤー(Android TVSDK)の特定のメディアタイプに対するCENCの暗号化が破損しました。 |
| PTPUB-954 | サンプル —AES暗号化は、デフォルトではAAXS DRMをバイパスします。また、リモートキー配信が有効な状態でスローされるエラーもあります。 |
| PTPUB-951 | Widevineでkey_file_pathが指定されていない場合、Offline Packagerでは例外がスローされません。 代わりにNPEをスローします。 |

Primetime Packagerの最新ドキュメントは、[https://help.adobe.com/en_US/primetime/api/packagers/index.html](https://help.adobe.com/en_US/primetime/api/packagers/index.html)で入手できます。

### バージョン2.3.1 {#known-issue-in-version}の既知の問題

このリリースには、次の問題が存在します。

| **問題番号** | **説明** |
|---|---|
| PTPUB-1005 | AAXS DRM用に生成された最終設定レベルの.mpdファイルで、PlaylistCreatorが.psshファイルの正しいURLを提供しません。 |
| PTPUB-1001 | in_pathパラメーターを介して空のパスが提供される場合、PlaylistCreatorはエラーをスローする必要があります |
| PTPUB-990 | DASHの場合、Offline Packagerは、`log_vi` &amp; `iv_out_path`のパラメーターが指定されているときに、Packagerで生成されたIVをディスクに書き込みません。 |
| PTPUB-980 | 構成ファイルをパッケージ化に使用する場合、パラメーター`key_url`を使用しても、指定された入力から引用符は削除されません。 |

## Adobe Primetimeオフラインパッケージャー2.3.1 {#adobe-primetime-offline-packager}

### 最小システム要件{#minimum-system-requirements}

サポートされるオペレーティングシステム

* Linux CentOS 6.3 64ビット

ハードウェア要件

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）

* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）

* ハードディスク

(Disk-SAS):最小10 GB(7.5K RPM)

（ディスク —SSD）:400 MBps読み取り/書き込み速度

(NAS):1 GB専用リンク

ソフトウェア要件

* OracleJava SE 1.8以降

### Adobe Primetimeオフラインパッケージャー2.3.1 {#adobe-primetime-offline-packager-1}

1. [Oracleのサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava SEソフトウェアをダウンロードし、インストール手順に従います。
1. `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip`という名前のAdobe PrimetimeOffline Packager 2.3.1アーカイブファイルをディスクに展開します。

### Offline Packager 2.3.1の設定{#configuring-the-offline-packager}

設定手順については、[https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)のPrimetime Offline Packager使用の手引きガイドを参照してください

## Primetime Offline Packager 2.1（2015年7月）の新機能{#what-s-new-in-primetime-offline-packager-july}

PlayReady BuyDRMのサポート（DASHの場合） 詳しくは、[ヘルプドキュメント](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)を参照してください。

Offline Packagerの機能強化には、次のものも含まれています。

PTPUB-780 EXT-X-開始タグのサポートを追加

## Primetime Offline Packager 2.0（2015年6月）の新機能{#what-s-new-in-primetime-offline-packager-june}

Clear DASH output supportが追加されました。 詳しくは、製品ドキュメント[ここ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)を参照してください。

このリリースでは、次の問題も修正されました。

* PTPUB-783 Offline Packagerで、空のWebVTTファイルを処理できるようになりました。
* PTPUB- 781特定のトランスコードされたMP4アセットがオフラインパッケージャーでパッケージ化され、MBR出力が生成される場合の、Chrome上のHLS出力内のアーティファクト。

## Adobe Primetimeオフラインパッケージャ2.1 {#adobe-primetime-offline-packager-2}

### 最小システム要件{#minimum-system-requirements-1}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）

* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）

* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）

* ハードディスク

   * (Disk-SAS):最小10 GB(7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み速度
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* OracleJava SE 1.8以降

### Offline Packager 2.1のインストール{#installing-offline-packager}

1. [Oracleのサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava SEソフトウェアをダウンロードし、インストール手順に従います。
1. `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`をディスクに展開します。

### Offline Packager 2.1の設定{#configuring-the-offline-packager-1}

[https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)で利用可能な設定の詳細については、Primetime Offline Packager使用の手引きドキュメントを参照してください。

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。
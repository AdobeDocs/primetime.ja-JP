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

---


# Primetime Offline Packagerのリリース {#primetime-offline-packager-x-releases}

Primetime Offline Packager 2.1および2.3.1リリースの新機能

## Primetime Offline Packager 2.3.1の新機能（2016年10月） {#what-s-new-in-primetime-offline-packager-oct}

このリリースでは、MPEG-DASHのオンデマンドプロファイルが有効になり、PlaylistCreatorツールのサポートが追加され、以下に示すMulti-DRMシナリオに関する主な修正がいくつか行われました。 `validate`

| **問題番号** | **説明** |
|---|---|
| PTPUB-985 | HLS AAXSとSample-AESは、パッケージャーで生成されたキーに対しては機能しません。 |
| PTPUB-973 | 特定のWidevineコンテンツの暗号化アルゴリズムのエラーを修正しました。 |
| PTPUB-964 | 特定のプレーヤー(Android TVSDK)の特定のメディアタイプに対するCENCの暗号化が解除されました。 |
| PTPUB-954 | サンプル —AES暗号化は、リモートキー配信が有効な場合に発生するデフォルト/エラーにより、AAXS DRMをバイパスします。 |
| PTPUB-951 | Widevineでkey_file_pathが指定されていない場合、Offline Packagerでは例外が発生しません。 代わりにNPEをスローします。 |

Primetime Packagerの最新ドキュメントは、https://help.adobe.com/en_US/primetime/api/packagers/index.htmlで入手で [きます](https://help.adobe.com/en_US/primetime/api/packagers/index.html)。

### バージョン2.3.1の既知の問題 {#known-issue-in-version}

このリリースには、次の問題が存在します。

| **問題番号** | **説明** |
|---|---|
| PTPUB-1005 | AAXS DRM用に生成された最終的な設定レベル.mpdファイルで、PlaylistCreatorが.psshファイルの正しいURLを提供しない。 |
| PTPUB-1001 | in_pathパラメーターを介して空のパスが指定された場合、PlaylistCreatorはエラーをスローする |
| PTPUB-990 | DASHの場合、パラメーター `log_vi` &amp;が指定されていると、Offline PackagerはPackagerで生成されたIVをディスクに書き込み `iv_out_path` ません。 |
| PTPUB-980 | 設定ファイルをパッケージ化に使用する場合、パラメーターを使 `key_url` 用しても、指定された入力から引用符は削除されません。 |

## Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager}

### 必要システム構成 {#minimum-system-requirements}

サポートされるオペレーティングシステム

* Linux CentOS 6.3 64ビット

ハードウェア要件

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）

* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）

* ハードディスク

(Disk-SAS):最低10 GB (7.5K RPM)

（ディスク —SSD）:400 MBpsの読み取り/書き込み速度

(NAS):1 GB専用リンク

ソフトウェア要件

* Oracle Java SE 1.8以降

### Adobe Primetime Offline Packager 2.3.1 {#adobe-primetime-offline-packager-1}

1. Java SEソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
1. この名前のAdobe Primetime Offline Packager 2.3.1アーカイブファイルをディスク `PrimetimeOfflinePackager-2-3-1-b47-10142016.zip` に展開します。

### Offline Packager 2.3.1の設定 {#configuring-the-offline-packager}

設定手順については、https://help.adobe.com/en_US/primetime/api/packagers/offline/index.htmlの『Primetime Offline Packagerはじめに』ガイドを参照してくだ [さい。](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## Primetime Offline Packager 2.1（2015年7月）の新機能 {#what-s-new-in-primetime-offline-packager-july}

PlayReady BuyDRMのサポート（DASH用）。 詳しくは、ここで利用可能なヘルプドキュメントを参 [照してくださ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)い。

また、オフラインパッケージャーの機能が強化されました。

PTPUB-780 EXT-X-STARTタグのサポートを追加

## Primetime Offline Packager 2.0（2015年6月）の新機能 {#what-s-new-in-primetime-offline-packager-june}

DASH出力のクリアのサポートが追加されました。 詳しくは、製品のドキュメ [ント](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html) を参照してください。

このリリースでは、次の問題も修正されました。

* PTPUB-783 Offline Packagerで、空のWebVTTファイルを処理できるようになりました。
* PTPUB- 781特定のトランスコードされたMP4アセットがオフラインパッケージャーでパッケージ化され、MBR出力が生成される場合の、Chrome上のHLS出力のアーティファクト。

## Adobe Primetime Offline Packager 2.1 {#adobe-primetime-offline-packager-2}

### 必要システム構成 {#minimum-system-requirements-1}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）

* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）

* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）

* ハードディスク

   * (Disk-SAS):最低10 GB (7.5K RPM)
   * （ディスク —SSD）:400 MBpsの読み取り/書き込み速度
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* Oracle Java SE 1.8以降

### Offline Packager 2.1のインストール {#installing-offline-packager}

1. Java SEソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
1. をディスク `Adobe Primetime - Offline Packager 2.1.0 archive file, PrimetimeOfflinePackager-2-1-0-b15-07082015.zip`に展開します。

### Offline Packager 2.1の設定 {#configuring-the-offline-packager-1}

https://help.adobe.com/en_US/primetime/api/packagers/offline/index.htmlで利用可能な設定の詳細については、『Primetime Offline Packagerはじめに』を参照してくだ [さい。](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。
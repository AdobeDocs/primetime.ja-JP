---
title: Primetime Streaming Serverのリリース
seo-title: Primetime Streaming Server 1.xリリース
description: Primetime Streaming Server 1.3および1.4リリースの新機能。
seo-description: Primetime Streaming Server 1.3および1.4リリースの新機能。
uuid: be05db6b-713f-4406-940d-9f3a805f967b
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: baec714e-9d41-4e8b-b134-13a736885cbd
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Primetime Streaming Serverのリリース {#primetime-streaming-server-x-releases}

Primetime Streaming Server 1.3および1.4リリースの新機能。

## Primetime Streaming Server 1.4の新機能（12月のリリース） {#what-s-new-in-primetime-streaming-server-december-release}

**Offline Packager**

* 出力HLSストリームにMPEG-2 TSに存在するID3メタデータが含まれるようになりました。
* HLSオーディオのみのストリームに、静的な画像を関連付けることができるようになりました
* HLS AES暗号化ワークフローのユーザー入力としてIVを提供するためのサポート
* オフラインパッケージャーでIVが生成された場合に、IVをファイルに出力する機能をサポート
* プレイリストクリエイターで、複数言語のオーディオグループと複数言語のWebVTT字幕グループのメディアストリームへの関連付けがサポートされるようになりました。

**オリジンサーバー**

* HLS AES暗号化は、ライブおよびVODワークフローで使用できます。 Primetime Originは、受信するHLSストリームまたはMP4ファイルにHLS AES暗号化を適用できます。
* また、JIT HLS AES暗号化を、受信するHDSストリームをHLSストリームに変換する際に使用することもできます。
* Primetime Originで、PHLSストリームのSWFホワイトリストをサポートするようになりました。 以前は、PHDSストリームに対してのみサポートされていました

**Primetime Live Packager**

* 入力RTMPおよびMPEG-2 TSストリーム用のHLS AES-128ストリームの生成のサポート

PHDS/PHLS証明書が更新されました。 同じ有効期限は2016年10月1日です。

### **リリース1.4に含まれているバグ修正**{#bug-fixes-included-in-release}

* PTPUB-282- OfflinePackager 1.3.1で作成されたHLSセットレベルマニフェストには、コーデックと解像度の情報が含まれていません。
* PTPUB-353 - PlayListCreatorは、設定レベルマニフェストへのWebVTT情報の追加をサポートしていません
* PTPUB-583:PlaylistCreatorツールが予期せずグループURIの先頭に追加される。
* PTPUB-605プレイリストクリエーターが各バリアントストリームの字幕グループをリストしない
* PTPUB-634 - Offline Packagerは、マニフェストにSpliceInsertを追加します。
* PTPUB-635 — 単一の広告キュー用に複数のSpliceOutタグが挿入されます。

### リリース1.4の既知の問題 {#known-issue-in-release}

* PTPUB- 645 DPISimpleモードは、両方のコマンドラインキューとインストリームキューが両方ともオフラインパッケージャーの設定で提供されている場合に、DPIScte35モードが指定されていても強制的に実行されます。

## Primetime Streaming Server 1.3.1の新機能（5月のリリース） {#what-s-new-in-primetime-streaming-server-may-release}

バージョン1.3.1は、ホットフィックスを参照します。 JIT MP4の主なパフォーマンスの強化で構成されているので、お客様に推奨されるアップグレード機能を次の点で強化しました。

1. キーの回転を含むDRMを使用した元のMP4 JIT m3u8生成のパフォーマンス修正
1. MP4 JIT変換用に生成されたフラグメントURIに、JITマニフェストリクエストからクエリパラメーターをコピーするための設定「CopyQueryParamToJITFragmentURIs」を追加しました。 使用例については、HTTP Origin Serverのドキュメントを参照してください
1. vod.xmlに追加されたConfig/MP4Only設定を使用して、JIT変換用の拡張子のないMP4ファイルを許可する

### リリース1.3.1に含まれているバグ修正 {#bug-fixes-included-in-release-1}

* 3759167：パッケージ化時のタイムスタンプの異常が原因で、すべてのSCTE35キューが出力マニフェストに含まれるわけではありません。 SCTE35メッセージのSpliceInfoSectionのTimeSignalのSpliceTimeにpts_adjustmentを適用します。

### リリース1.3.1の既知の問題 {#known-issues-in-release}

* 3717039：パッケージャーがDPI単純モードキューを生成するように設定されている場合、実際には、スプライスの挿入や配置の機会など、特定の信号タイプを探し、単純モードキューにのみ変換する必要があります。 プログラムの起動、ネットワークの起動など、他のタイプの信号は無視する必要があります。

* 3718598:HSMアクセスを有効にして保護されたコンテンツを提供するようにOrigin Serverが設定されている場合、バックエンドLunaSAクライアントはHSMモジュールと頻繁に通信します。

## Primetime Streaming Server 1.3（4月リリース）の新機能 {#what-s-new-in-primetime-streaming-server-april-release}

Primetime 1.3リリースは、ストリーミングコンテンツに関する新機能、操作性とセキュリティが向上しました。

**Live PackagerとOrigin Serverの統合フォームとしてのPrimetime Streaming Server**

Primetime Live PackagerとPrimetime Originが統合され、単一のコンポーネントとして機能します。 このコンポーネントは、PackagerまたはOriginとして使用するか、組み合わされた機能を使用して、ライブストリームをパッケージ化およびホストすることができます。

これにより、これらのサーバに統合されたファイルインターフェイスが提供され、1台のマシン上での実行が容易になります。 引き続き、別のPackagerまたはOriginとして設定できる柔軟性が提供されます。

**ベータMPEG-DASHのサポート**

Primetime Streaming Serverは、ライブおよびVODワークフロー用のMPEG-DASHパッケージをサポートしています。 Live Packagerコンポーネントは、取り込み先のRTMPまたはMPEG-2-TSストリームをDASH形式に変換します。 OriginコンポーネントはDASHストリームを受け付けます。

VODワークフローの場合、Offline PackagerコンポーネントはMP4およびTSアセットをMPEG-DASH ISOBFF形式に変換します。

**ライブからVODへのコンバージョン**

新しいコンポーネントの記録サーバーが使用可能になり、ライブストリームのキャプチャとVOD再生用のアーカイブをサポートするようになりました。 フルイベント再生の作成、およびイベントの一部のクリップ/ハイライトの作成をサポートします。 オーディオ専用ストリームの記録、広告の削除またはライブコンテンツのスレートを設定できます。 レコーディングサーバは、Primetime Streaming ServerとサードパーティOriginsと連携します。

**Primetime Live PackagerでのRTMPからHLSへの変換**

Primetime Live Packagerコンポーネントは、RTMPストリームからのHLSストリームの作成をサポートします。 また、Primetime DRMと保護されたストリーミングを出力HLSストリームに追加することもできます。

**Primetime Live Packagerへの着信RTMPストリームの認証**

usermgmt.jarにPrimetime Live Packagerが付属し、RTMPストリームをPrimetime Live Packagerに送信する際に、信頼できる秘密鍵証明書を使用してアクセスを設定できるようになりました。

これで、ストリームをLive Packagerに送信する際に、ユーザー名とパスワードを使用するようにエンコーダーを設定できます。

**HDSおよびHLS用のトップレベルマニフェストを作成するPlaylistCreatorツール**

Primetime Offline Packagerで利用できる便利なユーティリティPlaylistCreator.jarが追加され、HDSおよびHLSアセット用のトップレベルのマニフェストファイルを簡単に作成できるようになりました。

**ハードウェアセキュリティモジュールを組み込むための追加のセキュリティ機能**

Primetime Offline Packagerで、ハードウェアセキュリティモジュールからPackagerの秘密鍵証明書と共通キーへのアクセスがサポートされるようになりました。

ハードウェアセキュリティモジュールは、これらの機密資産をさらに保護します。

**VODパッケージのパフォーマンスの向上**

Primetime Offline Packagerの中間アセットのパッケージ化時間を改善するため、いくつかのパフォーマンスの強化が組み込まれました。

**JIT MP4パッケージのパフォーマンスの向上**

VODアセットの大きなライブラリに対するユーザーの要求を処理するために、Primetime OriginのJITパッケージ化機能にいくつかのパフォーマンスが強化されました。

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### 必要システム構成 {#minimum-system-requirements}

**ネットワーク要件**

* MPEG-TSストリームをエンコーダーからLive Packagerに送信するには、ネットワークをマルチキャストに対応させる必要があります。 また、Live Packagerは、マルチキャストネットワークを必要としないエンコーダーからRTMPストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最低10 GB (7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* Oracle Java JRE 1.7(推奨：Sun/Oracle Hotspot JVM)。 JMX APIへのJConsoleアクセスにはJDKが必要です

### Primetime Streaming Serverのインストールと設定 {#install-and-configure-primetime-streaming-server}

**ストリーミングサーバのインストール**

1. Java SEおよびJDKソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
2. Adobe Primetime-Streaming Server 1.4アーカイブファイルをディスク `Primetime- StreamingServer-1-4-0-b206-12042014.zip` に展開します。

**Primetimeストリーミングサーバの起動**

ストリーミングサーバを起動するには、ストリーミングサーバのルートディレクトリにあるコマンドラインで次のコマンドを実行します。\
`$./pss_start.sh`

**Live PackagerまたはHTTP Origin ServerとしてのPrimetime Streaming Serverの設定**

ストリーミングサーバーをLive PackagerまたはOrigin Serverとして設定するには、ストリーミングサーバーのルートディレクトリ内のconfディレクトリに配置されたps.xml設定ファイルを更新します。

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Primetimeストリーミングサーバの停止**

ストリーミングサーバを停止するには、ストリーミングサーバのルートディレクトリで次のコマンドを実行します。\
`$./pss_stop.sh`

**Primetimeストリーミングサーバーの再起動**

ストリーミングサーバを再起動するには、ストリーミングサーバを停止して起動します。

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Primetime Streaming Serverのアンインストール**

ストリーミングサーバをアンインストールするには、ストリーミングサーバを停止し、Primetimeディレクトリ内のストリーミングサーバのpssディレクトリを削除します

## Live PackagerとOrigin Server 1.4の使用 {#working-with-live-packager-and-origin-server}

この節は、Primetime Streaming Serverを使用せず、代わりにPrimetime Live Packagerおよび/またはPrimetime Origin Serverをデプロイする場合に適用されます

### 必要システム構成 {#minimum-system-requirements-1}

**ネットワーク要件**

* MPEG-TSストリームをエンコーダーからLive Packagerに送信するには、ネットワークをマルチキャストに対応させる必要があります。 また、Live Packagerは、マルチキャストネットワークを必要としないエンコーダーからRTMPストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最低10 GB (7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* Oracle Java JRE 1.7(推奨：Sun/Oracle Hotspot JVM)。 JMX APIへのJConsoleアクセスにはJDKが必要です

上記の最小必要システム構成は、Live PackagerだけでなくOrigin Serverにも当てはまります。

### Live Packagerのインストールと設定 {#install-and-configure-the-live-packager}

**Live Packagerのインストール**

1. Java SEおよびJDKソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
1. Adobe Primetime - Live Packager 1.4アーカイブファイルをディスク `Primetime-LivePackager-1-4-0-b206-12042014.zip` に展開します。

**HTTP Origin Serverのインストール**

1. Java JREおよびJDKソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
1. Adobe Primetime - HTTP Origin Server 1.4アーカイブファイルをディスク `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`に展開します。

**Live Packagerを起動するには** 、Packagerを起動するには、Packagerのルートディレクトリから次のコマンドを実行します。\
`$packager_start.sh`

**HTTP Origin Serverを起動するには**

HTTP Origin Serverを起動するには、Origin Serverのルートディレクトリにあるコマンドラインから次のコマンドを実行します。\
`$./origin_start.sh`

**Live Packagerの停止**

パッケージャーを停止するには、パッケージャーのルートディレクトリから次のコマンドを実行します。\
`$packager_stop.sh`

**HTTP Origin Serverの停止**

HTTP Origin Serverを停止するには、Origin Serverのルートディレクトリで次のコマンドを実行します。\
`$./origin_stop.sh`

**Live Packagerの再起動**

Packagerを再起動するには、Packagerを停止して起動します。

**注意**:パッケージャーを起動すると、一時ディレクトリ内のフラグメントターゲットからブートストラップ情報の初期化が試行されます。 フラグメントターゲットでブートストラップ情報が見つかった場合は、パッケージャーが再起動されたことを意味します。 再起動の場合、パッケージャーは次のフラグメントの境界まで待機し、パッケージ化を開始します。 パッケージャーは、見つからないフラグメントがあることを示すギャップエントリをブートストラップに挿入します。

**HTTP Origin Serverの再起動**

HTTP Origin Serverを再起動するには、HTTP Origin Serverを停止して起動します。

**Live Packagerの設定**

配布ファイルには、パッケージャーのテストに使用できるサンプル設定が含まれています。

Adobe Primetime - Live Packager 1.4アーカイブを展開した後、ディレクトリをpackagerディレクトリに変更し、packager_start.shスクリプトを実行します。 サンプル設定では、マルチキャストアドレス239.235.0.3:14000をリッスンし、ローカルオリジンサーバーをポート8080で実行します。 出力がに書き込まれるように設定されま `packager/webroot/_default_/_default_/ directory`す。

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**HTTP Origin Serverの設定**

ここで利用可能な設定の詳細については、『Primetime HTTP Origin Serverはじめに』を参照してください。

**Live Packagerのアンインストール**

Packagerをアンインストールするには、Packagerを停止し、PrimetimeディレクトリからPackagerディレクトリを削除します。

**HTTP Origin Serverのアンインストール**

HTTP Origin Serverをアンインストールするには、HTTP Origin Serverを停止し、Primetimeディレクトリ内のHTTP Origin Serverのhttporiginディレクトリを削除します。

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### 必要システム構成 {#minimum-system-requirements-2}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最低10 GB (7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* Oracle Java JRE 1.7以降。

### Offline Packagerのインストールと設定 {#install-and-configure-offline-packager}

Offline Packagerをインストールするには、次の手順に従います。

1. Java SEソフトウェアを [Oracleサイトからダウンロードし](https://www.oracle.com/technetwork/java/javase/downloads/index.html) 、インストール手順に従います。
1. Adobe Primetime - Offline Packager 1.4アーカイブファイルをディスク `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`に展開します。

ここで利用可能な設定の詳細については、『Primetime Offline Packagerはじめに』を参照して [ください](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)。

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。
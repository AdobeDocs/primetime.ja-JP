---
title: Primetime Streaming Serverのリリース
description: Primetime Streaming Server 1.3および1.4リリースの新機能。
products: SG_PRIMETIME
topic-tags: release-notes
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---


# Primetime Streaming Serverリリース{#primetime-streaming-server-x-releases}

Primetime Streaming Server 1.3および1.4リリースの新機能。

## Primetime Streaming Server 1.4の新機能（12月リリース） {#what-s-new-in-primetime-streaming-server-december-release}

**Offline Packager**

* 出力HLSストリームに、MPEG-2 TSに存在するID3メタデータが含まれるようになりました。
* HLSオーディオのみのストリームに静的な画像を関連付けることができるようになりました
* HLS AES暗号化ワークフローのユーザー入力としてIVを提供するためのサポート
* オフラインパッケージャーでIVが生成された場合にIVをファイルに出力する機能をサポート
* プレイリストクリエイターで、複数言語オーディオグループと複数言語WebVTTの字幕グループのメディアストリームへの関連付けがサポートされるようになりました

**接触チャネルサーバ**

* HLS AES暗号化は、LiveおよびVODワークフローで使用できます。 Primetime接触チャネルは、Just in Timeで、受信するHLSストリームまたはMP4ファイルにHLS AES暗号化を適用できます。
* また、受信したHDSストリームをHLSストリームに変換する際に、JIT HLS AES暗号化を適用することもできます。
* Primetime接触チャネルで、PHLSストリームのSWF許可リストがサポートされるようになりました。 以前は、PHDSストリームに対してのみサポートされていました

**Primetime Live Packager**

* 入力RTMPおよびMPEG-2 TSストリーム用のHLS AES-128ストリームの生成のサポート

PHDS/PHLS証明書が更新されました。 同じ新しい有効期限は2016年10月1日です。

### **リリース1.4に含まれているバグ修正** {#bug-fixes-included-in-release}

* PTPUB-282- OfflinePackager 1.3.1で作成されたHLSセットレベルマニフェストには、コーデックと解像度の情報が含まれていません。
* PTPUB-353 - PlayListCreatorは、設定レベルマニフェストへのWebVTT情報の追加をサポートしていません
* PTPUB-583 - PlaylistCreatorツールが予期せずグループURIの先頭に付加される。
* PTPUB-605プレイリストクリエーターで、各バリアントストリームの字幕グループがリストされない
* PTPUB-634 -Offline Packagerは、SpliceInsertをマニフェストに追加します。
* PTPUB-635 — 単一の広告キュー用に複数のSpliceOutタグが挿入されます。

### リリース1.4の既知の問題{#known-issue-in-release}

* PTPUB- 645 DPISimpleモードは、コマンドラインキューとインストリームキューの両方がオフラインパッケージャーの設定で提供されている場合に、DPIScte35モードが指定されている場合でも強制されます。

## Primetime Streaming Server 1.3.1（5月リリース）の新機能{#what-s-new-in-primetime-streaming-server-may-release}

バージョン1.3.1は、修正プログラムを参照しています。 次の強化点は、JIT MP4の主なパフォーマンス強化事例で構成されているので、お客様向けに推奨されるアップグレードになっています。

1. DRMとの接触チャネル時のMP4 JIT m3u8生成のパフォーマンス修正（キーの回転を含む）
1. JITマニフェストリクエストからMP4 JIT変換用に生成されたフラグメントURIにクエリパラメーターをコピーするための設定「CopyQueryParamToJITFragmentURIs」が追加されました。 使用例については、HTTP接触チャネルサーバーのドキュメントを参照してください
1. vod.xmlに追加されたConfig/MP4Only設定経由の、JIT変換の拡張子のないMP4ファイルを許可する

### リリース1.3.1 {#bug-fixes-included-in-release-1}に含まれているバグ修正

* 3759167 — パッケージ化時のタイムスタンプの異常が原因で、一部のSCTE35キューが出力マニフェストに到達しない場合があります。 SCTE35メッセージのSpliceInfoSectionのTimeSignalのSpliceTimeにpts_adjustmentを適用します。

### リリース1.3.1 {#known-issues-in-release}の既知の問題

* 3717039 — パッケージャーがDPI単純モードキューを生成するように設定されている場合、スプライス挿入や配置のオポチュニティなど、特定の信号タイプを探し、単純モードキューに変換する必要があります。 プログラム開始、ネットワーク開始など、他の種類の信号は無視する必要があります。

* 3718598 -接触チャネルサーバーがHSMアクセスで保護されたコンテンツを提供するように設定されている場合、バックエンドLunaSAクライアントはHSMモジュールと頻繁に通信します。

## Primetime Streaming Server 1.3（APRILリリース）の新機能{#what-s-new-in-primetime-streaming-server-april-release}

Primetime 1.3リリースでは、ストリーミングコンテンツに関する新機能、操作性とセキュリティが向上しています。

**Live Packagerと接触チャネルサーバーの統合フォームとしてのPrimetime Streaming Server**

Primetime Live PackagerとPrimetime接触チャネルが統合され、1つのコンポーネントとして機能します。 このコンポーネントは、Packagerや接触チャネルーとして使用することも、組み合わされた機能を使用してLive Streamをパッケージ化し、ホストすることもできます。

これにより、これらのサーバに統合されたファイルインターフェイスが提供され、単一のマシン上での実行が容易になります。 Packagerと接触チャネルを別々に設定する柔軟性も引き続き提供されます。

**ベータ版MPEG- DASHのサポート**

Primetime Streaming Serverは、ライブおよびVODワークフロー用のMPEG-DASHパッケージをサポートします。 Live Packagerコンポーネントは、取り込み先のRTMPまたはMPEG-2-TSストリームをDASH形式に変換します。 接触チャネルコンポーネントはDASHストリームを受け付けます。

VODワークフローの場合、Offline PackagerコンポーネントはMP4およびTSアセットをMPEG-DASH ISOBFF形式に変換します。

**ライブからVODへの変換**

ライブストリームのキャプチャとVOD再生用のアーカイブをサポートする新しいコンポーネントレコーディングサーバーが利用できるようになりました。 フルイベント再生の作成、およびイベントの一部のクリップ/ハイライトの作成をサポートします。 オーディオ専用ストリームの記録、広告の削除、ライブコンテンツのスレートを設定できます。 記録サーバは、Primetime Streaming Serverおよびサードパーティの接触チャネルと連携します。

**Primetime Live PackagerでのRTMPからHLSへの変換**

Primetime Live Packagerコンポーネントは、RTMPストリームからのHLSストリームの作成をサポートします。 また、Primetime DRMおよび保護されたストリーミングを出力HLSストリームに追加することもできます。

**Primetime Live Packagerへの着信RTMPストリームの認証**

usermgmt.jarにPrimetime Live Packagerが付属し、RTMPストリームをPrimetime Live Packagerに送信する際に、信頼できる資格情報を使用してアクセスを設定できるようになりました

これで、ストリームをLive Packagerに送信する際に、ユーザー名とパスワードを使用するようにエンコーダーを設定できます。

**HDSおよびHLS用のトップレベルマニフェストを作成するPlaylistCreatorツール**

Primetime Offline Packagerで高度なユーティリティPlaylistCreator.jarが利用可能になり、HDSおよびHLSアセット用のトップレベルのマニフェストファイルを簡単に作成できます。

**ハードウェアセキュリティモジュールを組み込むための追加のセキュリティ機能**

Primetime Offline Packagerで、ハードウェアセキュリティモジュールからPackagerの資格情報証明書と共通キーにアクセスできるようになりました。

ハードウェアセキュリティモジュールは、これらの機密資産をさらに保護します。

**VODパッケージのパフォーマンスの向上**

Primetime Offline Packagerのメザニンアセットのパッケージ化に要する時間を改善するため、パフォーマンスがいくつか強化されました。

**JIT MP4パッケージのパフォーマンスの向上**

Primetime接触チャネルのJITパッケージ化機能には、大規模なVODアセットのライブラリに対するユーザーの要求に対処するため、パフォーマンスがいくつか強化されました。

## Adobe Primetimeストリーミングサーバ1.4 {#adobe-primetime-streaming-server}

### 最小システム要件{#minimum-system-requirements}

**ネットワーク要件**

* MPEG-TSストリームをエンコーダーからLive Packagerに送信するには、ネットワークをマルチキャストに対応させる必要があります。 Live Packagerは、マルチキャストネットワークを必要としないエンコーダーからもRTMPストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最小10 GB(7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7(推奨：Sun/OracleホットスポットJVMを参照)。 JConsoleがJMX APIにアクセスするには、JDKが必要です

### Primetime Streaming Serverのインストールと設定{#install-and-configure-primetime-streaming-server}

**ストリーミングサーバのインストール**

1. [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava SEおよびJDKソフトウェアをダウンロードし、インストール手順に従います。
2. Adobe Primetimeストリーミングサーバ1.4アーカイブファイル`Primetime- StreamingServer-1-4-0-b206-12042014.zip`をディスクに展開します。

**Primetimeストリーミングサーバの開始**

ストリーミングサーバを開始するには、ストリーミングサーバのルートディレクトリにあるコマンドラインで次のコマンドを実行します。\
`$./pss_start.sh`

**Live PackagerまたはHTTP接触チャネルサーバーとしてのPrimetime Streaming Serverの設定**

ストリーミングサーバーをLive Packagerまたは接触チャネルサーバーとして設定するには、ストリーミングサーバーのルートディレクトリのconfディレクトリにあるpss.xml設定ファイルを更新します。

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Primetimeストリーミングサーバーの停止**

ストリーミングサーバを停止するには、ストリーミングサーバのルートディレクトリで次のコマンドを実行します。\
`$./pss_stop.sh`

**Primetimeストリーミングサーバーの再起動**

ストリーミングサーバを再起動するには、ストリーミングサーバを停止して開始します。

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Primetime Streaming Serverのアンインストール**

ストリーミングサーバをアンインストールするには、ストリーミングサーバを停止し、Primetimeディレクトリ内のストリーミングサーバのpssディレクトリを削除します

## Live Packagerと接触チャネルサーバー1.4の操作{#working-with-live-packager-and-origin-server}

この節は、Primetime Streaming Serverを使用せず、代わりにPrimetime Live PackagerやPrimetime接触チャネルサーバーをデプロイする場合に適用されます

### 最小システム要件{#minimum-system-requirements-1}

**ネットワーク要件**

* MPEG-TSストリームをエンコーダーからLive Packagerに送信するには、ネットワークをマルチキャストに対応させる必要があります。 Live Packagerは、マルチキャストネットワークを必要としないエンコーダーからもRTMPストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最小10 GB(7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7(推奨：Sun/OracleホットスポットJVMを参照)。 JConsoleがJMX APIにアクセスするには、JDKが必要です

上記の最小必要システム構成は、Live Packagerだけでなく、接触チャネルサーバーにも当てはまります。

### Live Packagerのインストールと設定{#install-and-configure-the-live-packager}

**Live Packagerのインストール**

1. [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava SEおよびJDKソフトウェアをダウンロードし、インストール手順に従います。
1. Adobe Primetime- Live Packager 1.4アーカイブファイル`Primetime-LivePackager-1-4-0-b206-12042014.zip`をディスクに展開します。

**HTTP接触チャネルサーバーのインストール**

1. [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava JREおよびJDKソフトウェアをダウンロードし、インストール手順に従います。
1. Adobe Primetime- HTTP接触チャネルサーバ1.4アーカイブファイル`Primetime-HttpOrigin-1-4-0-b206-12042014.zip`をディスクに展開します。

**Live** Packagerを開始するにはPackagerを開始するには、Packagerのルートディレクトリから次のコマンドを実行します。\
`$packager_start.sh`

**HTTP接触チャネルサーバーを開始するには**

HTTP接触チャネルサーバーを開始するには、接触チャネルサーバーのルートディレクトリにあるコマンドラインで次のコマンドを実行します。\
`$./origin_start.sh`

**Live Packagerの停止**

Packagerを停止するには、Packagerのルートディレクトリで次のコマンドを実行します。\
`$packager_stop.sh`

**HTTP接触チャネルサーバーの停止**

HTTP接触チャネルサーバーを停止するには、接触チャネルサーバーのルートディレクトリで次のコマンドを実行します。\
`$./origin_stop.sh`

**Live Packagerの再起動**

Packagerを再起動するには、Packagerを停止して開始します。

**注意**:Packagerの開始は、一時ディレクトリ内のフラグメントターゲットからブートストラップ情報を初期化しようとします。フラグメントターゲットでブートストラップ情報が見つかった場合は、パッケージャーが再起動されたことを意味します。 再起動の場合、パッケージャーは次のフラグメント境界まで待機し、次に開始のパッケージ化を待ちます。 パッケージャーは、ブートストラップに欠落しているフラグメントがあることを示すギャップのエントリを挿入します。

**HTTP接触チャネルサーバーの再起動**

HTTP接触チャネルサーバーを再起動するには、HTTP接触チャネルサーバーを停止して開始します。

**Live Packagerの設定**

配布ファイルには、パッケージャーのテストに使用できるサンプル設定が含まれています。

Adobe Primetime- Live Packager 1.4アーカイブを抽出した後、ディレクトリをpackager開始に変更し、packager_directory.shスクリプトを実行します。 サンプル設定では、マルチキャストアドレス239.235.0.3:14000をリッスンし、ローカル接触チャネルサーバーをポート8080で実行します。 出力は`packager/webroot/_default_/_default_/ directory`に書き込まれるように設定されます。

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**HTTP接触チャネルサーバーの設定**

ここで利用可能な設定の詳細については、Primetime HTTP接触チャネルサーバーの概要ドキュメントを参照してください。

**Live Packagerのアンインストール**

Packagerをアンインストールするには、Packagerを停止し、PrimetimeディレクトリからPackagerのディレクトリを削除します。

**HTTP接触チャネルサーバーのアンインストール**

HTTP接触チャネルサーバーをアンインストールするには、HTTP接触チャネルサーバーを停止し、Primetimeディレクトリ内のHTTP接触チャネルサーバーのhttproginディレクトリを削除します。

## Adobe Primetimeオフラインパッケージャ1.4 {#adobe-primetime-offline-packager}

### 最小システム要件{#minimum-system-requirements-2}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64ビット

**ハードウェア要件**

* 3.2 GHz Intel® Pentium® 4プロセッサー（デュアルIntel Xeon®以上を推奨）
* 64ビットオペレーティングシステム：4 GBのRAM（8 GBを推奨）
* 1 Gbイーサネットカードを推奨（複数のネットワークカードと10 Gbもサポート）
* ディスク：

   * (Disk-SAS):最小10 GB(7.5K RPM)
   * （ディスク —SSD）:400 MBps読み取り/書き込み
   * (NAS):1 GB専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7以降。

### Offline Packagerのインストールと設定{#install-and-configure-offline-packager}

Offline Packagerをインストールするには、次の手順に従います。

1. [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html)からJava SEソフトウェアをダウンロードし、インストール手順に従います。
1. Adobe Primetime- Offline Packager 1.4アーカイブファイル`Primetime- OfflinePackager-1-4-0-b206-12042014.zip`をディスクに展開します。

[ここ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html)で利用可能な設定の詳細については、Primetime Offline Packager使用の手引きドキュメントを参照してください。

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。
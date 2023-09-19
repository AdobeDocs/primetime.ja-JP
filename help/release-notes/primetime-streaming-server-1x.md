---
title: Primetime ストリーミングサーバのリリース
description: Primetime Streaming Server 1.3 および 1.4 リリースの新機能。
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---

# Primetime ストリーミングサーバのリリース {#primetime-streaming-server-x-releases}

Primetime Streaming Server 1.3 および 1.4 リリースの新機能。

## Primetime Streaming Server 1.4（12 月リリース）の新機能 {#what-s-new-in-primetime-streaming-server-december-release}

**オフライン Packager**

* 出力 HLS ストリームに MPEG-2 TS に存在する ID3 メタデータが含まれるようになりました。
* HLS オーディオのみのストリームに、関連付けられた静的画像を含めることができるようになりました。
* HLS AES 暗号化ワークフローのユーザー入力として IV を提供するサポート
* オフラインパッケージャによって IV が生成された場合のファイルへの IV 出力のサポート
* プレイリストクリエイターで、複数言語のオーディオグループと複数言語の WebVTT サブタイトルグループのメディアストリームへの関連付けがサポートされるようになりました。

**オリジンサーバー**

* HLS AES 暗号化は、ライブワークフローと VOD ワークフローで使用できます。 Primetime Origin は、Just in Time で受信 HLS ストリームまたは MP4 ファイルに HLS AES 暗号化を適用できます。
* また、受信 HDS ストリームを HLS ストリームに変換する際に、JIT HLS AES 暗号化を適用することもできます。
* Primetime Origin で、PHLS ストリームのSWF許可リストへの登録がサポートされるようになりました。 以前は、PHDS ストリームでのみサポートされていました。

**Primetime Live Packager**

* 入力 RTMP および MPEG-2 TS ストリーム用の HLS AES-128 ストリームの生成のサポート

PHDS/PHLS 証明書が更新されました。 同じの新しい有効期限は10/01/2016です。

### **リリース 1.4 に含まれるバグ修正** {#bug-fixes-included-in-release}

* PTPUB-282- OfflinePackager 1.3.1 で作成された HLS セットレベルマニフェストにコーデックと解像度の情報が含まれていません。
* PTPUB-353 - PlayListCreator は、設定レベルのマニフェストに WebVTT 情報を追加することをサポートしていません
* PTPUB-583 - PlaylistCreator ツールが予期せずグループ URI の前に追加される。
* PTPUB-605 プレイリスト作成者が各バリアントストリームのサブタイトルグループをリストしていません
* PTPUB-634 — オフラインパッケージャはマニフェストに SpliceInsert を追加します。
* PTPUB-635 — 単一の広告キューに対して挿入された複数の SpliceOut タグ。

### リリース 1.4 の既知の問題 {#known-issue-in-release}

* PTPUB-645 DPISimple モードは、コマンドラインキューとインストリームキューの両方がオフラインパッケージャ設定で提供されている場合に、 DPIScte35 モードが指定されている場合でも、強制的に使用されます

## Primetime Streaming Server 1.3.1（5 月リリース）の新機能 {#what-s-new-in-primetime-streaming-server-may-release}

バージョン 1.3.1 は、ホットフィックスを表します。 JIT MP4 の主なパフォーマンス強化で構成されているので、次の機能強化により、お客様に推奨されるアップグレードになります。

1. DRM によるオリジンでの MP4 JIT m3u8 の生成に対するキーの回転を含むパフォーマンス修正
1. JIT マニフェストリクエストのクエリパラメーターを MP4 JIT 変換用に生成されたフラグメント URI にコピーするための設定「CopyQueryParamToJITFragmentURIs」が追加されました。 使用例については、 HTTP Origin Server のドキュメントを参照してください
1. vod.xml に追加された Config/MP4Only 設定を使用して、JIT 変換用の拡張子のない MP4 ファイルを許可します。

### リリース 1.3.1 に含まれるバグ修正 {#bug-fixes-included-in-release-1}

* 3759167 — パッケージ化時のタイムスタンプの異常が原因で、すべての SCTE35 キューが出力マニフェストに出力されるわけではありません。 SCTE35 メッセージの SpliceInfoSection の TimeSignal で、SpliceTime に pts_adjustment を適用します。

### リリース 1.3.1 の既知の問題 {#known-issues-in-release}

* 3717039 — パッケージャが DPI シンプルモードキューを生成するように設定されている場合、実際には、スプライスの挿入や配置の機会など、特定の信号タイプを探し、それらのみをシンプルモードキューに変換する必要があります。 プログラムの開始、ネットワークの開始など、他のタイプのシグナルは無視する必要があります。

* 3718598 - HSM アクセスを有効にして保護されたコンテンツを提供するように Origin Server が設定されている場合、バックエンド LunaSA クライアントは HSM モジュールと頻繁に通信を行います

## Primetime Streaming Server 1.3（4 月リリース）の新機能 {#what-s-new-in-primetime-streaming-server-april-release}

Primetime 1.3 リリースでは、ストリーミングコンテンツ、より優れた操作性、セキュリティに関する新機能がいくつか追加されました。

**Live Packager と Origin Server の統合形式としての Primetime Streaming Server**

Primetime Live Packager と Primetime Origin が統合され、単一のコンポーネントとして機能します。 このコンポーネントは、パッケージャーとして、または接触チャネルとして使用するか、組み合わされた機能を使用してライブストリームをパッケージ化し、ホストすることができます。

これにより、これらのサーバに統合されたファイルインターフェイスが提供され、1 台のマシンで簡単に実行できます。 これにより、引き続き個別のパッケージャまたは接触チャネルとして設定できる柔軟性が提供されます。

**ベータ MPEG - DASH のサポート**

Primetime Streaming Server は、ライブおよび VOD ワークフロー用の MPEG-DASH パッケージをサポートしています。 Live Packager コンポーネントは、取り込み RTMP または MPEG-2-TS ストリームを DASH 形式に変換します。 Origin コンポーネントは DASH ストリームを受け付けます。

VOD ワークフローの場合、オフラインパッケージャコンポーネントは MP4 および TS アセットを MPEG-DASH ISOBFF 形式に変換します。

**ライブから VOD へのコンバージョン**

ライブストリームのキャプチャと VOD 再生のアーカイブをサポートする新しいコンポーネントの記録サーバーを使用できるようになりました。 フルイベント再生の作成、およびイベントの一部のクリップやハイライトをサポートします。 オーディオ専用ストリームの記録、広告の削除、ライブコンテンツのスレートの記録をおこなうように設定できます。 Recording Server は、Primetime ストリーミングサーバーと、サードパーティのオリジンと連携します。

**Primetime Live Packager での RTMP から HLS への変換**

Primetime Live Packager コンポーネントは、RTMP ストリームからの HLS ストリームの作成をサポートしています。 また、出力 HLS ストリームに Primetime DRM と保護されたストリーミングを追加することもできます。

**Primetime Live パッケージャへの受信 RTMP ストリームの認証**

usermgmt.jar に Primetime Live Packager が付属し、RTMP ストリームを Primetime Live Packager に送信する際に、信頼できる資格情報でアクセスを設定できるようになりました。

これで、Live Packager にストリームを送信する際に、ユーザー名とパスワードを使用するようにエンコーダーを設定できます。

**HDS および HLS 用のトップレベルマニフェストを作成する PlaylistCreator ツール**

Primetime Offline Packager で、HDS および HLS アセット用のトップレベルのマニフェストファイルを簡単に作成できる、高機能なユーティリティ PlaylistCreator.jar を使用できるようになりました。

**ハードウェアセキュリティモジュールを組み込むための追加のセキュリティ機能**

Primetime Offline Packager で、ハードウェアセキュリティモジュールから Packager の資格情報証明書と共通キーへのアクセスがサポートされるようになりました。

ハードウェアセキュリティモジュールは、これらの機密資産に対する追加の保護を提供します。

**VOD パッケージのパフォーマンスの向上**

Primetime Offline Packager のメザニンアセットのパッケージ化時間を改善するために、パフォーマンスがいくつか強化されました。

**JIT MP4 パッケージのパフォーマンスの向上**

VOD アセットの大規模なライブラリに対するユーザーリクエストを処理するため、Primetime Origin の JIT パッケージ機能にいくつかのパフォーマンス強化が組み込まれました。

## Adobe Primetime Streaming Server 1.4 {#adobe-primetime-streaming-server}

### 最小必要システム構成 {#minimum-system-requirements}

**ネットワーク要件**

* MPEG-TS ストリームをエンコーダーから Live Packager に送信するには、ネットワークでマルチキャストを有効にする必要があります。 また、Live Packager は、マルチキャストネットワークを必要としないエンコーダーから RTMP ストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64 ビット

**ハードウェア要件**

* 3.2GHz Intel® Pentium® 4 プロセッサー ( デュアル Intel Xeon®以上を推奨 )
* 64 ビットオペレーティングシステム： 4GB の RAM（8GB を推奨）
* 1 Gb イーサネットカードを推奨（複数のネットワークカードと 10 Gb もサポート）
* ディスク：

   * (Disk-SAS) :7,500 RPM で最低 10GB
   * (Disk-SSD) : 400MBps の読み取り/書き込み
   * (NAS) :1 GB の専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7 ( 推奨：Sun/Oracleホットスポット JVM)。 JMX API への JConsole アクセスには JDK が必要です

### Primetime ストリーミングサーバーのインストールと設定 {#install-and-configure-primetime-streaming-server}

**ストリーミングサーバーのインストール**

1. からの Java SE および JDK ソフトウェアのダウンロード [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
2. Adobe Primetime-Streaming Server 1.4 アーカイブファイルを抽出します。 `Primetime- StreamingServer-1-4-0-b206-12042014.zip` をディスクに追加します。

**Primetime ストリーミングサーバーの起動**

ストリーミングサーバを起動するには、ストリーミングサーバのルートディレクトリにあるコマンドラインから次のコマンドを実行します。\
`$./pss_start.sh`

**Primetime ストリーミングサーバーを Live Packager または HTTP Origin Server として設定する**

ストリーミングサーバーをライブパッケージャまたはオリジンサーバーとして構成するには、ストリーミングサーバーのルートディレクトリにある conf ディレクトリに配置された pss.xml 構成ファイルを更新します。

```
<Config> 
<!-- Set this false to disable the Origin Component. --> 
<OriginEnabled&gt;true&lt;/OriginEnabled>  
<!-- Set this false to disable the Packager Component. -->  
<PackagerEnabled&gt;true&lt;/PackagerEnabled>
</Config>
```

**Primetime ストリーミングサーバーを停止**

ストリーミングサーバを停止するには、ストリーミングサーバのルートディレクトリで次のコマンドを実行します。\
`$./pss_stop.sh`

**Primetime ストリーミングサーバーの再起動**

ストリーミングサーバを再起動するには、ストリーミングサーバを停止して起動します。

<!-- 

Comment Type: draft

**Configuring Primetime Streaming Server**

Refer the Primetime Streaming Server Getting Started document for the configuration details available at [https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf](https://help.adobe.com/en_US/primetime/platform/primetime_streaming_server.pdf).

-->

**Primetime ストリーミングサーバーのアンインストール**

ストリーミングサーバをアンインストールするには、ストリーミングサーバを停止し、Primetime ディレクトリ内のストリーミングサーバの pss ディレクトリを削除します。

## Live Packager と Origin Server 1.4 の使用 {#working-with-live-packager-and-origin-server}

この節の内容は、Primetime ストリーミングサーバーが使用されておらず、代わりに Primetime Live Packager AND/OR Primetime Origin Server がデプロイされている場合に適用されます

### 最小必要システム構成 {#minimum-system-requirements-1}

**ネットワーク要件**

* MPEG-TS ストリームをエンコーダーから Live Packager に送信するには、ネットワークでマルチキャストを有効にする必要があります。 また、Live Packager は、マルチキャストネットワークを必要としないエンコーダーから RTMP ストリームを受け付けます。

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64 ビット

**ハードウェア要件**

* 3.2GHz Intel® Pentium® 4 プロセッサー ( デュアル Intel Xeon®以上を推奨 )
* 64 ビットオペレーティングシステム： 4GB の RAM（8GB を推奨）
* 1 Gb イーサネットカードを推奨（複数のネットワークカードと 10 Gb もサポート）
* ディスク：

   * (Disk-SAS) :7,500 RPM で最低 10GB
   * (Disk-SSD) : 400MBps の読み取り/書き込み
   * (NAS) :1 GB の専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7 ( 推奨：Sun/Oracleホットスポット JVM)。 JMX API への JConsole アクセスには JDK が必要です

上記の最小必要システム構成は、Origin Server と Live Packager に当てはまります。

### Live Packager のインストールと設定 {#install-and-configure-the-live-packager}

**Live Packager のインストール**

1. からの Java SE および JDK ソフトウェアのダウンロード [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
1. Adobe Primetime - Live Packager 1.4 アーカイブファイルを抽出します。 `Primetime-LivePackager-1-4-0-b206-12042014.zip` をディスクに追加します。

**HTTP Origin Server のインストール**

1. から Java JRE および JDK ソフトウェアをダウンロードします。 [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
1. Adobe Primetime - HTTP Origin Server 1.4 アーカイブファイルを抽出します。 `Primetime-HttpOrigin-1-4-0-b206-12042014.zip`をディスクに追加します。

**Live Packager を起動するには、以下を実行します。** Packager を起動するには、Packager のルートディレクトリから次のコマンドを実行します。\
`$packager_start.sh`

**HTTP Origin Server を起動するには**

HTTP Origin Server を起動するには、Origin Server のルートディレクトリにあるコマンドラインから次のコマンドを実行します。\
`$./origin_start.sh`

**Live Packager を停止します。**

パッケージャを停止するには、パッケージャのルートディレクトリから次のコマンドを実行します。\
`$packager_stop.sh`

**HTTP オリジンサーバーを停止します。**

HTTP Origin Server を停止するには、Origin Server のルートディレクトリで次のコマンドを実行します。\
`$./origin_stop.sh`

**Live Packager を再起動します。**

Packager を再起動するには、Packager を停止して起動します。

**注意**：パッケージャーが起動すると、フラグメントターゲットのブートストラップ情報を一時ディレクトリに初期化しようとします。 フラグメントのターゲットにブートストラップ情報が見つかった場合は、パッケージャーが再起動されたことを示しています。 再起動の場合、パッケージャは次のフラグメントの境界まで待機し、パッケージ化を開始します。 パッケージャは、ブートストラップに空白のエントリを挿入し、見つからないフラグメントがあることを示します。

**HTTP オリジンサーバーを再起動します。**

HTTP Origin Server を再起動するには、HTTP Origin Server を停止して起動します。

**Live Packager の設定**

配布ファイルには、パッケージャのテストに使用できるサンプル設定が含まれています。

Adobe Primetime - Live Packager 1.4 アーカイブを展開した後、ディレクトリを packager ディレクトリに変更し、packager_start.sh スクリプトを実行します。 サンプル設定は、マルチキャストアドレス 239.235.0.3:14000をリッスンし、ローカルのオリジンサーバーをポート 8080 で実行します。 出力が `packager/webroot/_default_/_default_/ directory`.

<!-- 

Comment Type: draft

For more details about the configuration refer [the Primetime Live Packager document](https://help.adobe.com/en_US/primetime/api/packagers/index.html).

-->

**HTTP オリジンサーバーの設定**

設定の詳細については、 Primetime HTTP Origin Server はじめにのドキュメントを参照してください。

**Live Packager のアンインストール**

Packager をアンインストールするには、Packager を停止し、Primetime ディレクトリから Packager ディレクトリを削除します。

**HTTP Origin Server のアンインストール**

HTTP オリジンサーバーをアンインストールするには、HTTP オリジンサーバーを停止し、Primetime ディレクトリ内の HTTP オリジンサーバーの httpporigin ディレクトリを削除します。

## Adobe Primetime Offline Packager 1.4 {#adobe-primetime-offline-packager}

### 最小必要システム構成 {#minimum-system-requirements-2}

**サポートされるオペレーティングシステム**

* Linux CentOS 6.3 64 ビット

**ハードウェア要件**

* 3.2GHz Intel® Pentium® 4 プロセッサー ( デュアル Intel Xeon®以上を推奨 )
* 64 ビットオペレーティングシステム： 4GB の RAM（8GB を推奨）
* 1 Gb イーサネットカードを推奨（複数のネットワークカードと 10 Gb もサポート）
* ディスク：

   * (Disk-SAS) :7,500 RPM で最低 10GB
   * (Disk-SSD) : 400MBps の読み取り/書き込み
   * (NAS) :1 GB の専用リンク

**ソフトウェア要件**

* OracleJava JRE 1.7 以降。

### オフラインパッケージャのインストールと設定 {#install-and-configure-offline-packager}

Offline Packager をインストールするには、次の手順に従います。

1. Java SE ソフトウェアを [Oracleサイト](https://www.oracle.com/technetwork/java/javase/downloads/index.html) をクリックし、インストール手順に従います。
1. Adobe Primetime - Offline Packager 1.4 アーカイブファイルを抽出します。 `Primetime- OfflinePackager-1-4-0-b206-12042014.zip`をディスクに追加します。

使用可能な設定の詳細については、 Primetime Offline Packager の概要を参照してください [ここ](https://help.adobe.com/en_US/primetime/api/packagers/offline/index.html).

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。

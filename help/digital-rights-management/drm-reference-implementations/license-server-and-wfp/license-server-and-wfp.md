---
description: リファレンス実装サーバーは、Adobe Primetime DRM Java SDKのすべての機能を使用する完全な機能を持つライセンスサーバーの作成に役立ちます。
seo-description: リファレンス実装サーバーは、Adobe Primetime DRM Java SDKのすべての機能を使用する完全な機能を持つライセンスサーバーの作成に役立ちます。
seo-title: ライセンスサーバ
title: ライセンスサーバ
uuid: 39cb0d0f-f3dc-48e9-b6fd-6960a9ade291
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# ライセンスサーバ {#license-server}

リファレンス実装サーバーは、Adobe Primetime DRM Java SDKのすべての機能を使用する完全な機能を持つライセンスサーバーの作成に役立ちます。

この実装では、データベース内のユーザーエントリに基づいてユーザーが認証されます。 このサーバーには、ライセンスを発行するためのデモビジネスロジックが含まれており、Flash Media Rights Management Server 1.0および1.5の互換性サポートを提供します。

## ライセンスサーバの要件 {#license-server-requirements}

ライセンスサーバの要件：

* Tomcat 6.0以降のインストール
* データベース（MySQLなど）をインストールします(DVDに収録 [!DNL Third Party\MySQL])。
* Java 1.6以降がインストールされていることを確認します。
* サンプルのビルドスクリプトを実行するには、Ant 1.8以降があることを確認します

TomcatおよびMySQLのインストール後、必要なDRM資格情報のセットについてアドビに問い合わせてください。

## ライセンスサーバーの構築 {#build-the-license-server}

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>ライセンスサーバーの構築は、ソースコードを変更する場合にのみ必要です。 評価の目的で、出荷時のWARファイルを使用するだけで済みます。

参照実装ライセンスサーバーには、すべてのライセンスサーバーのソースコード( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`)と、ビジネスニーズに合わせてライセンスサーバーをカスタマイズできるAntビルドスクリプト( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`)が含まれています。

1. Ant構築スクリプトを変更して、Primetime DRM SDK、Tomcat、MySQLおよびLog4Jの場所を指定します。

   テキストエデ [!DNL build-refimpl.xml] ィターでファイルを開き、次のプロパティ値を設定します。

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Ant構築スクリプトが存在するディレ `all` クトリ内の、プロパティを持つAnt構築スクリプトを実行します。

   ```
   ant -f build-refimpl.xml all
   ```

   Ant構築スクリプトは、サーバーのWARフ [!DNL refimpl-build/wars] ァイルを含むディレクトリを作成します。

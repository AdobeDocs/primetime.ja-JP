---
description: リファレンス実装サーバーは、Adobe PrimetimeDRM Java SDKのすべての機能を使用する完全な機能を備えたライセンスサーバーの作成に役立ちます。
seo-description: リファレンス実装サーバーは、Adobe PrimetimeDRM Java SDKのすべての機能を使用する完全な機能を備えたライセンスサーバーの作成に役立ちます。
seo-title: ライセンスサーバー
title: ライセンスサーバー
uuid: 39cb0d0f-f3dc-48e9-b6fd-6960a9ade291
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# ライセンスサーバー {#license-server}

リファレンス実装サーバーは、Adobe PrimetimeDRM Java SDKのすべての機能を使用する完全な機能を備えたライセンスサーバーの作成に役立ちます。

この実装では、ユーザーはデータベース内のユーザーエントリに基づいて認証されます。 サーバには、ライセンス発行のためのデモビジネスロジックが含まれ、FlashメディアRights Managementサーバ1.0および1.5の互換性サポートを提供します。

## ライセンスサーバーの要件 {#license-server-requirements}

ライセンスサーバーの要件：

* Tomcat 6.0以降のインストール
* データベース（MySQLなど）をインストールします(DVDから入手可能、 [!DNL Third Party\MySQL])
* Java 1.6以降がインストールされていることを確認します
* サンプルのビルドスクリプトを実行するには、Ant 1.8以降を使用していることを確認します

TomcatとMySQLをインストールした後、必要なDRM秘密鍵証明書のセットについてAdobeに問い合わせてください。

## ライセンスサーバーの構築 {#build-the-license-server}

>[!NOTE]
>
>ライセンスサーバーの構築は、ソースコードを変更する場合にのみ必要です。 評価のために、出荷済みのWARファイルを使用するだけで済みます。

参照実装ライセンスサーバーには、すべてのライセンスサーバーのソースコード( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`)と、Antビルドスクリプト( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`)が含まれており、このスクリプトを使用して、ビジネスニーズに合わせてライセンスサーバーをカスタマイズできます。

1. Ant構築スクリプトを変更して、Primetime DRM SDK、Tomcat、MySQL、およびLog4Jの場所を指定します。

   テキストエディターで [!DNL build-refimpl.xml] ファイルを開き、次のプロパティ値を設定します。

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Ant構築スクリプトが存在するディレクトリ内の、 `all` プロパティを持つAnt構築スクリプトを実行します。

   ```
   ant -f build-refimpl.xml all
   ```

   Ant構築スクリプトは、サーバーのWARファイルを含む [!DNL refimpl-build/wars] ディレクトリを作成します。

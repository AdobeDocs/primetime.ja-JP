---
description: リファレンス実装サーバーは、Adobe PrimetimeDRM Java SDKのすべての機能を使用する完全な機能を備えたライセンスサーバーの作成に役立ちます。
title: ライセンスサーバー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---


# ライセンスサーバー{#license-server}

リファレンス実装サーバーは、Adobe PrimetimeDRM Java SDKのすべての機能を使用する完全な機能を備えたライセンスサーバーの作成に役立ちます。

この実装では、ユーザーはデータベース内のユーザーエントリに基づいて認証されます。 サーバには、ライセンス発行のためのデモビジネスロジックが含まれ、FlashメディアRights Managementサーバ1.0および1.5の互換性サポートを提供します。

## ライセンスサーバの要件{#license-server-requirements}

ライセンスサーバーの要件：

* Tomcat 6.0以降のインストール
* データベースをインストールします(例： MySQL （DVDで入手可能、[!DNL Third Party\MySQL]にあります）
* Java 1.6以降がインストールされていることを確認します
* サンプルのビルドスクリプトを実行するには、Ant 1.8以降を使用していることを確認します

TomcatとMySQLをインストールした後、必要なDRM秘密鍵証明書のセットについてAdobeに問い合わせてください。

## ライセンスサーバー{#build-the-license-server}の構築

>[!NOTE]
>
>ライセンスサーバーの構築は、ソースコードを変更する場合にのみ必要です。 評価のために、出荷済みのWARファイルを使用するだけで済みます。

参照実装ライセンスサーバーには、すべてのライセンスサーバーソースコード(`([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`)と、Antビルドスクリプト(`[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`)が含まれており、このスクリプトを使用して、ビジネスニーズに合わせてライセンスサーバーをカスタマイズできます。

1. Ant構築スクリプトを変更して、Primetime DRM SDK、Tomcat、MySQL、およびLog4Jの場所を指定します。

   [!DNL build-refimpl.xml]ファイルをテキストエディターで開き、次のプロパティ値を設定します。

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. Ant構築スクリプトが存在するディレクトリで、`all`プロパティを指定してAnt構築スクリプトを実行します。

   ```
   ant -f build-refimpl.xml all
   ```

   Ant構築スクリプトは、サーバーのWARファイルを含む[!DNL refimpl-build/wars]ディレクトリを作成します。

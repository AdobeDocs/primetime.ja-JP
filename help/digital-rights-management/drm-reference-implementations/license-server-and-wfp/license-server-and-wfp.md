---
description: 参照実装サーバーは、Adobe Primetime DRM Java SDK のすべての機能を使用する、完全に機能するライセンスサーバーを作成するのに役立ちます。
title: ライセンスサーバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# ライセンスサーバー {#license-server}

参照実装サーバーは、Adobe Primetime DRM Java SDK のすべての機能を使用する、完全に機能するライセンスサーバーを作成するのに役立ちます。

この実装では、ユーザーはデータベース内のユーザーエントリに基づいて認証されます。 このサーバには、ライセンスを発行するためのデモビジネスロジックが含まれ、FlashメディアRights Managementサーバ 1.0 および 1.5 の互換性サポートを提供します。

## ライセンスサーバーの要件 {#license-server-requirements}

ライセンスサーバの要件：

* Tomcat 6.0 以降のインストール
* データベース、例： MySQL （DVD に収録されている）を [!DNL Third Party\MySQL])
* Java 1.6 以降がインストールされていることを確認します。
* サンプルのビルドスクリプトを実行するには、Ant 1.8 以降が存在することを確認します。

Tomcat と MySQL をインストールした後、必要な DRM 資格情報のセットについてAdobeに問い合わせてください。

## ライセンスサーバーを構築します。 {#build-the-license-server}

>[!NOTE]
>
>ライセンスサーバーの構築は、ソースコードを変更する場合にのみ必要です。 評価のために、出荷された WAR ファイルを使用するだけで済みます。

参照実装ライセンスサーバには、すべてのライセンスサーバのソースコードが含まれています ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\src/`) と Ant ビルドスクリプト ( `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl/build-refimpl.xml`) を使用して、ビジネスニーズに合わせてライセンスサーバーをカスタマイズできます。

1. Ant ビルドスクリプトを変更して、Primetime DRM SDK、Tomcat、MySQL、および Log4J の場所を指定します。

   を開きます。 [!DNL build-refimpl.xml] ファイルを編集し、次のプロパティ値を設定します。

   * `sdkdir`
   * `tomcatdir`
   * `mysqldir`
   * `log4jdir`

1. を使用して Ant ビルドスクリプトを実行します。 `all` プロパティ。Ant ビルドスクリプトが存在するディレクトリにあります。

   ```
   ant -f build-refimpl.xml all
   ```

   Ant ビルドスクリプトは、 [!DNL refimpl-build/wars] サーバーの WAR ファイルを含むディレクトリ。

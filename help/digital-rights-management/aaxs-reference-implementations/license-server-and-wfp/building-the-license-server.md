---
seo-title: ライセンスサーバーの構築
title: ライセンスサーバーの構築
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# ライセンスサーバーの構築 {#building-the-license-server}

リファレンス実装ライセンスサーバには、ライセンスサーバをデプロイするためのWARファイルが含まれています。 また、すべてのライセンスサーバーのソースコードとAntビルドスクリプト(Reference Implementation\Server\refimpl\build-refimpl.xml)も含まれているので、コードを簡単に変更できます。

>[!NOTE]
>
>この手順は、ソースコードを変更する場合にのみ必要です。 評価のために、この手順をスキップし、出荷済みのWARファイルを使用できます。

Antスクリプトを実行する前に、スクリプトを変更して、AdobeアクセスSDK、Tomcat、MySQL、およびLog4Jの場所を指定します。 テキストエディターでbuild-refimpl.xmlを開き、プロパティの値を編集し `sdkdir, tomcatdir, mysqldir, and log4jdir`ます。 ソースコードをコンパイルし、参照実装用のWARファイルを作成するには、Antスクリプトを含むディレクトリ `ant -f build-refimpl.xml all` でを使用してスクリプトを実行します。 スクリプトが完了すると、サーバーのWARファイルを含む [!DNL refimpl-build/wars] ディレクトリが作成されます。

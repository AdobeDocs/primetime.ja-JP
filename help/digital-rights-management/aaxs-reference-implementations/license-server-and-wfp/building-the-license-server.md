---
title: ライセンスサーバーの構築
description: ライセンスサーバーの構築
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# ライセンスサーバーの構築 {#building-the-license-server}

参照実装ライセンスサーバには、ライセンスサーバを展開するための WAR ファイルが含まれています。 また、すべてのライセンスサーバーのソースコードと Ant ビルドスクリプト ( リファレンスImplementation\Server\refimpl\build-refimpl.xml) も含まれているので、コードを簡単に変更できます。

>[!NOTE]
>
>この手順は、ソースコードを変更する場合にのみ必要です。 評価のために、この手順をスキップし、出荷時の WAR ファイルを使用できます。

Ant スクリプトを実行する前に、スクリプトを変更して、Adobeアクセス SDK、Tomcat、MySQL、および Log4J の場所を指定します。 build-refimpl.xml をテキストエディターで開き、プロパティの値を編集します。 `sdkdir, tomcatdir, mysqldir, and log4jdir`. ソースコードをコンパイルし、参照実装用の WAR ファイルを作成するには、次を使用してスクリプトを実行します。 `ant -f build-refimpl.xml all` Ant スクリプトを含むディレクトリ内。 スクリプトが完了すると、 [!DNL refimpl-build/wars] サーバーの WAR ファイルを含むディレクトリが作成されます。

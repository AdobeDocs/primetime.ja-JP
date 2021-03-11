---
title: ライセンスサーバーの構築
description: ライセンスサーバーの構築
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---


# ライセンスサーバーの構築{#building-the-license-server}

リファレンス実装ライセンスサーバには、ライセンスサーバをデプロイするためのWARファイルが含まれています。 また、すべてのライセンスサーバーのソースコードとAntビルドスクリプト(Reference Implementation\Server\refimpl\build-refimpl.xml)も含まれているので、コードを簡単に変更できます。

>[!NOTE]
>
>この手順は、ソースコードを変更する場合にのみ必要です。 評価のために、この手順をスキップし、出荷済みのWARファイルを使用できます。

Antスクリプトを実行する前に、スクリプトを変更して、AdobeアクセスSDK、Tomcat、MySQL、およびLog4Jの場所を指定します。 build-refimpl.xmlをテキストエディターで開き、`sdkdir, tomcatdir, mysqldir, and log4jdir`プロパティの値を編集します。 ソースコードをコンパイルし、参照実装用のWARファイルを作成するには、Antスクリプトを含むディレクトリで`ant -f build-refimpl.xml all`を使用してスクリプトを実行します。 スクリプトが完了すると、サーバーのWARファイルを含む[!DNL refimpl-build/wars]ディレクトリが作成されます。

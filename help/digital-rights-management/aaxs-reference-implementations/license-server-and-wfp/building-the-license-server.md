---
seo-title: ライセンスサーバーの構築
title: ライセンスサーバーの構築
uuid: d7ca8a8f-c778-41a2-b823-93fac9ab07c5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバーの構築 {#building-the-license-server}

参照実装ライセンスサーバには、ライセンスサーバをデプロイするためのWARファイルが含まれています。 また、すべてのライセンスサーバーのソースコードとAntビルドスクリプト(リファレンスImplementation\Server\refimpl\build-refimpl.xml)も含まれているので、コードを簡単に変更できます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この手順は、ソースコードを変更する場合にのみ必要です。 評価のために、この手順をスキップし、出荷時のWARファイルを使用できます。

Antスクリプトを実行する前に、Adobe Access SDK、Tomcat、MySQLおよびLog4Jの場所を指定するようにスクリプトを変更します。 build-refimpl.xmlをテキストエディターで開き、プロパティの値を編集します `sdkdir, tomcatdir, mysqldir, and log4jdir`。 ソースコードをコンパイルし、参照実装のWARファイルを作成するには、Antスクリプトを含むディレクトリでを使 `ant -f build-refimpl.xml all` 用してスクリプトを実行します。 スクリプトが完了すると、サーバーのWAR [!DNL refimpl-build/wars] ファイルを含むディレクトリが作成されます。

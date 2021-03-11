---
title: データベースの設定とJNDIデータソースの設定
description: データベースの設定とJNDIデータソースの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# データベースの設定とJNDIデータソースの設定{#setting-up-the-database-and-configuring-the-jndi-datasource}

参照実装のライセンスサーバーでは、次の機能をサポートするデータベースが必要です。

* ユーザー認証
* 使用モデルデモビジネスルール
* メタデータ変換
* ドメインのサポート

匿名ライセンスの取得には、データベースを実行する必要はありません。

>[!NOTE]
>
>この節の説明は、Microsoft Windowsプラットフォーム向けです。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQLのドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQL 5.1.34をインストールして設定する必要があります。

1. MySQLインストーラーを実行します(DVDのThird Party\MySQL\Installer\5.1フォルダーにあります)。
1. インストール手順の最後に、**[!UICONTROL Configure MySQL Server Now]**&#x200B;をチェックして構成ウィザードを開始します。 デフォルトの設定を使用するか、テスト用に特定の設定を選択します。ただし、5番目の画面では&#x200B;**[!UICONTROL Online Transaction Processing (OLTP)]**&#x200B;または&#x200B;**[!UICONTROL Manual Setting]**&#x200B;を選択し、許容される最大接続数を入力する必要があります。

1. rootパスワードをメモしておきます。
1. MySQLを再インストールする必要がある場合は、次の手順に従って、後でサーバーを起動する際の問題を回避します。

   * フォルダー&#x200B;*システムドライブ* [!DNL \Documents and Settings\All Users\Application Data\MySQL]を削除します。

   * 古いMySQLインストールフォルダーを削除します。例えば、*システムドライブ：* [!DNL \Program Files\MySQL\MySQL Server 5.1]です。

次に、MySQL JDBC Driver 5.1.7をインストールする必要があります。これを行うには、[!DNL mysql-connector-java-5.1.7-bin.jar]（DVDの[!DNL Third Party\MySQL\Installer\5.1]フォルダーにある）をTomcat Server libディレクトリにコピーします。[!DNL ...\Tomcat6.0\lib]。

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7はTomcat 6.0で動作します。古いバージョンのTomcatはサポートされていません。

データベース・データベースを設定し、データベースにサンプル・データを入力して、サンプル・スキーマを設定します。 これを行うには、次の手順を実行します。

1. **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**&#x200B;に移動します。
1. パスワードを入力した後、次のSQLスクリプトを実行して、Webアプリケーションを介した接続を確立するためのユーザーアカウント`dbuser`を追加し、データベーススキーマを作成します（最後に「;」がないことを確認します）。 Enterキーを押すだけ)。

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. テスト用にデータが含まれるようにテーブルのサンプルデータを入力するスクリプトを編集します。[!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. このスクリプトを実行して、手順2と同様にデータを入力します。

>[!NOTE]
>
>[!DNL CreateSampleDB.sql]スクリプトを初めて実行すると、次のエラーが表示されます。

*エラー1396 (HY000):&#39;dbuser&#39;@&#39;localhost&#39;クエリOKの操作DROP USERが失敗しました。0行が影響を受けます（0.00秒）。*

このエラーは無視して構いません。 これは、このスクリプトを初めて実行したときにのみ発生します。

この時点で、データベース接続プール(DBCP)を設定する必要があります。 DBCPは、ジャカルタ — コモンズデータベース接続プールを使用します。 JNDI Datasource TestDBは、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続をlocalhost上にないMySQLサーバーを指すように変更するには、[!DNL flashaccess.war]にある[!DNL META-INF\context.xml]ファイル（ライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定）を変更するか、[!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml]を変更して、更新したファイルを使用してWARファイルを再作成します。 これらのパラメータを変更するには、WebContentディレクトリにある[!DNL context.xml]を編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソース設定を変更します。

Eclipse内でリファレンス実装プロジェクトをデバッグする場合は、実行/デバッグ設定に`$CATALINA_HOME\lib\tomcat-dbcp.jar`を追加する必要があります。 この手順は、スタンドアロンのTomcat 6.0サーバーで[!DNL flashaccess.war]ファイルを実行する場合は不要です。

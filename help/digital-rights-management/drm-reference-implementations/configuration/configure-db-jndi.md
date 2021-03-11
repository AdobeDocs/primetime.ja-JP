---
title: ライセンスサーバーデータベースの設定
description: ライセンスサーバーデータベースの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# ライセンスサーバーデータベースを設定{#configure-the-license-server-database}

データベース・スキーマを設定し、データベースにサンプル・データを入力して、サンプル・データベースを構成するには、次の手順を実行します。

1. MySQLコマンドラインを起動します。

   **Windowsの場合は —** クリック  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** >  **[!UICONTROL MySQL Server 5.1]** >  **[!UICONTROL MySQL Command Line Client]**

   **Linuxなどでは、**  — タイプ `MySQL`。

1. 次のSQLスクリプトを実行します。

   mysql>ソース&quot;`"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   次のスクリプトでは、ユーザーアカウント`dbuser`を追加し、Webアプリケーションを介した接続を確立し、データベーススキーマを作成します。

   >[!NOTE]
   >
   >スクリプトの最後にセミコロン(`;`)がないことを確認します。

1. テスト用のデータが含まれるように、テーブルにサンプルデータを入力する`PopulateSampleDB.sql`スクリプトを編集します。

   このスクリプトは`[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\`フォルダーにあります。
1. [!DNL PopulateSampleDB]スクリプトを実行し、手順2と同様にデータを入力します。

   >[!NOTE]
   >
   >[!DNL CreateSampleDB.sql]スクリプトを初めて実行すると、次のエラーが発生します。

   このエラーは無視して構いません。 このスクリプトを初めて実行したときにのみ発生します。

Jakarta-Commons Database Connection Poolを使用するDatabase Connection Pooling(DBCP)を設定する必要があります。 JNDI Datasource TestDBは、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続を変更して、localhost上にないMySQLサーバーを指すようにするには、次のいずれかのファイルを変更します。

* [!DNL META-INF\context.xml]ファイル。[!DNL flashaccess.war]ファイル内のライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定します。

* `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml`ファイル。

更新したファイルを使用してWARファイルを再作成します。

これらのパラメーターのいずれかを変更するには、[!DNL WebContent]ディレクトリの[!DNL context.xml]ファイルを編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソース設定を変更します。

Eclipseでリファレンス実装プロジェクトをデバッグする場合は、実行/デバッグ設定に`$CATALINA_HOME\lib\tomcat-dbcp.jar`を追加します。

>[!NOTE]
>
>スタンドアロンのTomcat 6.0サーバーで[!DNL flashaccess.war]ファイルを実行する場合は、この手順は不要です。


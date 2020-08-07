---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーデータベースの設定
title: ライセンスサーバーデータベースの設定
uuid: 6d34e849-1616-46bd-ad18-4f98e6c45af7
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# ライセンスサーバーデータベースの設定{#configure-the-license-server-database}

データベース・スキーマを設定し、データベースにサンプル・データを入力して、サンプル・データベースを構成するには、次の手順を実行します。

1. MySQLコマンドラインを起動します。

   **Windowsの場合は、** 「Click」 **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Linuxなどでは、**  — タイプ `MySQL`。

1. 次のSQLスクリプトを実行します。

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   次のスクリプトでは、ユーザーアカウントを追加し `dbuser`、Webアプリケーションを介した接続を確立し、データベーススキーマを作成します。

   >[!NOTE]
   >
   >スクリプトの最後にセミコロン( `;`)がないことを確認します。

1. テスト用のデータが含まれるようにテーブルのサンプルデータを入力する `PopulateSampleDB.sql` スクリプトを編集します。

   このスクリプトは `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` フォルダー内にあります。
1. 手順2と同様に、 [!DNL PopulateSampleDB] スクリプトを実行してデータを入力します。

   >[!NOTE]
   >
   >初めてスクリプトを実行すると、次の [!DNL CreateSampleDB.sql] エラーが発生します。

   このエラーは無視して構いません。 このスクリプトを初めて実行したときにのみ発生します。

Jakarta-Commons Database Connection Poolを使用するDatabase Connection Pooling(DBCP)を設定する必要があります。 JNDI Datasource TestDBは、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続を変更して、localhost上にないMySQLサーバーを指すようにするには、次のいずれかのファイルを変更します。

* フ [!DNL META-INF\context.xml] ァイル。ファイル内にあるライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定し [!DNL flashaccess.war] ます。

* フ `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` ァイル。

更新したファイルを使用してWARファイルを再作成します。

これらのパラメーターのいずれかを変更するには、 [!DNL context.xml][!DNL WebContent] ディレクトリ内のファイルを編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソース設定を変更します。

Eclipseでリファレンス実装プロジェクトをデバッグする場合は、実行/デバッグ設定 `$CATALINA_HOME\lib\tomcat-dbcp.jar` にを追加します。

>[!NOTE]
>
>スタンドアロンのTomcat 6.0サーバーで [!DNL flashaccess.war] ファイルを実行する場合は、この手順は不要です。


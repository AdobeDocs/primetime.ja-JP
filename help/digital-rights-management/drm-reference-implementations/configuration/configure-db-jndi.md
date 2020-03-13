---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーデータベースの設定
title: ライセンスサーバーデータベースの設定
uuid: 6d34e849-1616-46bd-ad18-4f98e6c45af7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバーデータベースの設定{#configure-the-license-server-database}

データベース・スキーマを設定し、データベースにサンプル・データを入力して、サンプル・データベースを構成する手順は、次のとおりです。

1. MySQLコマンドラインを表示します。

   **Windowsの場合は、** // **[!UICONTROL Window's Start Menu]** をクリッ **[!UICONTROL MySQL]** クします **[!UICONTROL MySQL Server 5.1]** 。 **[!UICONTROL MySQL Command Line Client]**

   **Linuxなど**  — タイプ `MySQL`。

1. 次のSQLスクリプトを実行します。

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   次のスクリプトでは、ユーザーアカウン `dbuser`トを追加し、Webアプリケーションを介した接続を確立し、データベーススキーマを作成します。

   >[!NOTE]
   >
   >スクリプトの最後にセミコロン( `;`)がないことを確認します。

1. テーブルにサン `PopulateSampleDB.sql` プルデータを入力し、テスト用のデータを含めるスクリプトを編集します。

   このスクリプトはフォルダー内にあ `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` ります。
1. 手順2と同 [!DNL PopulateSampleDB] 様に、スクリプトを実行してデータを入力します。

   >[!NOTE] {class=&quot;- topic/note &quot;}
   >
   >スクリプトを初めて実行すると、次の [!DNL CreateSampleDB.sql] エラーが発生します。

   このエラーは無視して構いません。 このスクリプトを初めて実行したときにのみ発生します。

Jakarta-Commonsデータベース接続プールを使用するデータベース接続プール(DBCP)を設定する必要があります。 JNDI Datasource TestDBは、このアプリケーションサーバーの接続プーリングを利用するように設定されています。 データベース接続を変更して、localhost上にないMySQLサーバーを指すようにするには、次のいずれかのファイルを変更します。

* ファ [!DNL META-INF\context.xml] イル。ファイル内にあるライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定し [!DNL flashaccess.war] ます。

* ファイ `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` ルです。

更新したファイルを使用してWARファイルを再作成します。

これらのパラメーターを変更するには、ディレ [!DNL context.xml] クトリ内のフ [!DNL WebContent] ァイルを編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソースの設定を変更します。

Eclipseで参照実装プロジェクトをデバッグする場合は、実行/ `$CATALINA_HOME\lib\tomcat-dbcp.jar` デバッグの設定にを追加します。

>[!NOTE]
>
>スタンドアロンのTomcat 6.0 [!DNL flashaccess.war] サーバーでファイルを実行する場合、この手順は不要です。


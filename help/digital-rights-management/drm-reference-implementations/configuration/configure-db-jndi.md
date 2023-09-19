---
title: ライセンスサーバーデータベースを設定する
description: ライセンスサーバーデータベースを設定する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# ライセンスサーバーデータベースを設定する{#configure-the-license-server-database}

データベース・スキーマを設定し、サンプル・データを使用してデータベースにデータを入力して、サンプル・データベースを構成する手順は、次のとおりです。

1. MySQL コマンドラインを表示します。

   **Windows の場合 —** クリック  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]**

   **Linux などの場合**  — タイプ `MySQL`.

1. 次の SQL スクリプトを実行します。

   mysql> source &quot; `"[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\createsampledb.sql" dbscript\createsampledb.sql`&quot;

   このスクリプトは、ユーザーアカウントを追加します `dbuser`が Web アプリケーションを介して接続を確立し、データベーススキーマを作成します。

   >[!NOTE]
   >
   >セミコロン ( `;`) をスクリプトの最後に配置します。

1. を編集します。 `PopulateSampleDB.sql` テスト用のデータを含めるようにテーブルのサンプルデータを入力するスクリプト。

   このスクリプトは、 `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\dbscript\ dbscript\` フォルダー。
1. を実行します。 [!DNL PopulateSampleDB] スクリプトを使用して、手順 2 と同様にデータを入力します。

   >[!NOTE]
   >
   >を初めて実行したとき [!DNL CreateSampleDB.sql] スクリプトに次のエラーが発生しました。

   このエラーは無視しても問題ありません。 このスクリプトを初めて実行したときにのみ発生します。

Jakarta-Commons データベース接続プールを使用する Database Connection Pooling（DBCP；データベース接続プール）を設定する必要があります。 JNDI Datasource TestDB は、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続を localhost 上にない MySQL サーバーを指すように変更するには、次のいずれかのファイルを変更します。

* The [!DNL META-INF\context.xml] ファイル：内のライセンスサーバのデータベースの場所、ユーザー名、およびパスワードを指定します。 [!DNL flashaccess.war] ファイル。

* The `[DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\refimpl\WebContent/META-INF\context.xml` ファイル。

更新されたファイルを使用して、WAR ファイルを再作成します。

これらのパラメーターのいずれかを変更するには、 [!DNL context.xml] ファイルを [!DNL WebContent] ディレクトリを作成し、Ant スクリプトを使用して WAR ファイルを再作成します。 データベースを調整するには、このファイルの JNDI データソース設定を変更します。

Eclipse で参照実装プロジェクトをデバッグする場合は、 `$CATALINA_HOME\lib\tomcat-dbcp.jar` を run/debug 設定に追加します。

>[!NOTE]
>
>次を実行した場合、 [!DNL flashaccess.war] ファイルをスタンドアロンの Tomcat 6.0 サーバー上に配置する場合、この手順は不要です。

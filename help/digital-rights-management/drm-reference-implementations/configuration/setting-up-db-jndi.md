---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーデータベースのセットアップ
title: ライセンスサーバーデータベースのセットアップ
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# ライセンスサーバーデータベース{#set-up-the-license-server-database}のセットアップ

参照実装のライセンスサーバーでは、次をサポートするデータベースが必要です。

* ユーザー認証
* 使用モデルデモビジネスルール
* メタデータ変換
* ドメインのサポート

匿名ライセンスの取得には、データベースが実行されている必要はありません。

>[!NOTE]
>
>この手順は、Microsoft Windowsにのみ適用されます。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQLのドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQLをインストールして設定する必要があります。

1. DVDの[!DNL Third Party\MySQL\Installer\5.1]フォルダーに移動し、インストールプログラムを開始します。
1. MySQLのインストールを完了します。
1. **[!UICONTROL Configure MySQL Server Now]**&#x200B;を選択して、構成ウィザードを開始します。
1. 5つ目の画面までは、デフォルト設定を使用するか、テスト用の特定の設定を選択します。
1. 5つ目の画面で、「**[!UICONTROL Online Transaction Processing (OLTP)]**」または「**[!UICONTROL Manual Setting]**」を選択し、許可される接続の最大数を入力します。
1. rootパスワードを書き留めます。
1. MySQLを再インストールするには、後でサーバーを開始する必要がある場合は、次の手順を実行します。
   1. *システムドライブ：*&#x200B;フォルダーを削除します。

      このフォルダーは[!DNL \Documents and Settings\All Users\Application Data\MySQL]にあります。
   1. 古いMySQLインストールフォルダーを削除します。

      例えば、*システムドライブ：*（[!DNL \Program Files\MySQL\MySQL Server 5.1]にあります）。
1. MySQL JDBC Driver 5.1.7をインストールするには、DVDの[!DNL Third Party\MySQL\Installer\5.1]フォルダーの[!DNL mysql-connector-java-5.1.7-bin.jar]ファイルをTomcatサーバーの[!DNL ...\Tomcat6.0\lib]ディレクトリにコピーします。

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7はTomcat 6.0で動作します。古いバージョンのTomcatはサポートされなくなりました。


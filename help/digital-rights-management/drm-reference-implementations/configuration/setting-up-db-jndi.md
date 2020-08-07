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


# ライセンスサーバーデータベースのセットアップ{#set-up-the-license-server-database}

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

1. DVDで、フォルダーに移動し、 [!DNL Third Party\MySQL\Installer\5.1] 開始ーにインストールプログラムを追加します。
1. MySQLのインストールを完了します。
1. 設定ウィザード **[!UICONTROL Configure MySQL Server Now]** を開始する場合に選択します。
1. 5つ目の画面までは、デフォルト設定を使用するか、テスト用の特定の設定を選択します。
1. 5つ目の画面で、「または」を選択 **[!UICONTROL Online Transaction Processing (OLTP)]****[!UICONTROL Manual Setting]** し、最大接続数を入力します。
1. rootパスワードを書き留めます。
1. MySQLを再インストールするには、後でサーバーを開始する必要がある場合は、次の手順を実行します。
   1. 次の *システムドライブを削除します。* フォルダ。

      このフォルダーはにあり [!DNL \Documents and Settings\All Users\Application Data\MySQL]ます。
   1. 古いMySQLインストールフォルダーを削除します。

      例えば、にある *システムドライブ*: [!DNL \Program Files\MySQL\MySQL Server 5.1]など。
1. MySQL JDBC Driver 5.1.7をインストールするには、DVD上の [!DNL mysql-connector-java-5.1.7-bin.jar] フォルダー内の [!DNL Third Party\MySQL\Installer\5.1] ファイルをTomcatサーバーの [!DNL ...\Tomcat6.0\lib] ディレクトリにコピーします。

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7はTomcat 6.0で動作します。古いバージョンのTomcatはサポートされなくなりました。


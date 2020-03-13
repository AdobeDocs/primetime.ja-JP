---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーデータベースの設定
title: ライセンスサーバーデータベースの設定
uuid: aa6185f2-8e9d-4b65-971a-b7534d910580
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバーデータベースの設定{#set-up-the-license-server-database}

参照実装ライセンスサーバーでは、次をサポートするデータベースが必要です。

* ユーザー認証
* 使用モデルデモビジネスルール
* メタデータの変換
* ドメインのサポート

匿名ライセンスの取得では、データベースが実行されている必要はありません。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この手順は、Microsoft Windowsにのみ適用されます。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQLのドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQLをインストールして設定する必要があります。

1. DVD上のフォルダーに移動し、インスト [!DNL Third Party\MySQL\Installer\5.1] ールプログラムを起動します。
1. MySQLのインストールを完了します。
1. 選択し **[!UICONTROL Configure MySQL Server Now]** て、設定ウィザードを起動します。
1. 5つ目の画面までは、デフォルト設定を使用するか、テスト用の特定の設定を選択します。
1. 5つ目の画面で、またはを選 **[!UICONTROL Online Transaction Processing (OLTP)]** 択し、 **[!UICONTROL Manual Setting]** 最大接続数を入力します。
1. rootのパスワードを書き留めます。
1. MySQLを再インストールするには、後でサーバーを起動する必要がある場合は、次の手順を実行します。
   1. システムドラ *イブの削除：* フォルダ。

      このフォルダーはにありま [!DNL \Documents and Settings\All Users\Application Data\MySQL]す。
   1. 古いMySQLインストールフォルダーを削除します。

      例えば、 *にあるシステム* drive：などです [!DNL \Program Files\MySQL\MySQL Server 5.1]。
1. MySQL JDBC Driver 5.1.7をインストールするには、DVD上のフ [!DNL mysql-connector-java-5.1.7-bin.jar] ォルダ内のフ [!DNL Third Party\MySQL\Installer\5.1] ァイルをTomcatサーバー上のデ [!DNL ...\Tomcat6.0\lib] ィレクトリにコピーします。

   >[!NOTE] {class=&quot;- topic/note &quot;}
   >
   >MySQL JDBC Driver 5.1.7は、Tomcat 6.0で動作します。古いバージョンのTomcatはサポートされなくなりました。


---
title: ライセンスサーバーデータベースを設定する
description: ライセンスサーバーデータベースを設定する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# ライセンスサーバーデータベースを設定する{#set-up-the-license-server-database}

参照実装ライセンスサーバーでは、以下をサポートするデータベースが必要です。

* ユーザー認証
* 使用状況モデルデモビジネスルール
* メタデータの変換
* ドメインのサポート

匿名ライセンスの取得では、データベースが実行されている必要はありません。

>[!NOTE]
>
>この手順は、Microsoft Windows にのみ適用されます。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQL のドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQL をインストールして設定する必要があります。

1. DVD で、に移動します。 [!DNL Third Party\MySQL\Installer\5.1] フォルダを開き、インストールプログラムを起動します。
1. MySQL のインストールを完了します。
1. 選択 **[!UICONTROL Configure MySQL Server Now]** をクリックして、設定ウィザードを起動します。
1. 5 番目の画面まで、デフォルト設定を使用するか、テスト用の特定の設定を選択します。
1. 5 番目の画面で、「 」を選択します。 **[!UICONTROL Online Transaction Processing (OLTP)]** または **[!UICONTROL Manual Setting]** 許可される接続の最大数を入力します。
1. ルートパスワードを書き留めます。
1. MySQL を再インストールするには、後でサーバーを起動する必要がある場合は、次の手順を実行します。
   1. を削除します。 *システムドライブ：* フォルダー。

      このフォルダーは、 [!DNL \Documents and Settings\All Users\Application Data\MySQL].
   1. 古い MySQL install フォルダーを削除します。

      例： *システムドライブ：*（内） [!DNL \Program Files\MySQL\MySQL Server 5.1].
1. MySQL JDBC Driver 5.1.7 をインストールするには、 [!DNL mysql-connector-java-5.1.7-bin.jar] ファイルを [!DNL Third Party\MySQL\Installer\5.1] DVD 上のフォルダを [!DNL ...\Tomcat6.0\lib] Tomcat サーバー上のディレクトリ。

   >[!NOTE]
   >
   >MySQL JDBC Driver 5.1.7 は、Tomcat 6.0 で動作します。古いバージョンの Tomcat はサポートされなくなりました。

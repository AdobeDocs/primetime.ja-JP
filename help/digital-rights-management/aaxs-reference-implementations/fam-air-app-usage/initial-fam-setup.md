---
title: Flash Accessマネージャの初期設定
description: Flash Accessマネージャの初期設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Flash Accessマネージャの初期設定 {#initial-flash-access-manager-setup}

次の手順を実行して、Flash Access・マネージャを設定します。

1. Packager サーバーをデプロイします。 このサーバーは、ファイアウォール内のユーザーのみが使用できる必要があります（このソフトウェアを公開コンピュータに展開しないでください）。 サーバーのデプロイについて詳しくは、 [ライセンスサーバーと監視フォルダーパッケージャのデプロイ](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * コピー [!DNL flashaccess-packager.war] を Tomcat の webapps フォルダーに追加します。
   * コピー [!DNL flashaccess-refimpl-packager.properties] リソースからクラスパス上の場所に移動します。
   * サーバーを起動します。 プロパティファイルの問題が原因でエラーが発生します。これは、プロパティがまだ入力されていないので、想定されている動作です。

1. 次を起動して、Flash AccessマネージャーAIRアプリケーションをインストールします。 [!DNL .air] ファイル (AIR 1.5 以降が必要 )
1. Flash AccessマネージャーAIRアプリケーションを起動します。

   サーバーが `https://localhost:8080*`に設定すると、アプリケーションがサーバーに接続できないことを示すエラーが表示されます。 エラーダイアログを閉じ、「環境設定」タブで Packager Server の URL に正しい URL を入力します。 サーバーが指定した URL で実行されていて、そのプロパティーファイルがクラスパス上にある場合、「環境設定」画面にプロパティーファイル内の値が入力されます。 Packager サーバーの URL を設定すると、AIRアプリケーションはこの設定を記憶するので、次回アプリケーションを起動する際にこの設定を入力する必要はありません。
1. 「環境設定」タブの値を入力し、 **[!UICONTROL Save]**.
1. 監視フォルダーを使用する場合は、手順 3 で見たエラーから回復するには、サーバーを再起動する必要があります。 環境設定が正しく設定されている場合は、起動時にエラーが表示されません。

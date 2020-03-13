---
description: 'null'
seo-description: 'null'
seo-title: Flash Access Managerの初期設定
title: Flash Access Managerの初期設定
uuid: e9041f7c-b098-4121-88bf-ff3e6369e01b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Flash Access Managerの初期設定 {#initial-flash-access-manager-setup}

Flash Access Managerを設定するには、次の手順を実行します。

1. Packagerサーバーをデプロイします。 このサーバは、ファイアウォール内のユーザーのみが使用できます（このソフトウェアをパブリックコンピュータに展開しないでください）。 サーバーのデプロイについて詳しくは、ライセンスサーバーと監視 [フォルダーのパッケージャーのデプロイを参照してくださ](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md)い。

   * TomcatのWebApps [!DNL flashaccess-packager.war] フォルダーにをコピーします。
   * リソース [!DNL flashaccess-refimpl-packager.properties] からクラスパス上の場所にコピーします。
   * サーバーを起動します。 プロパティファイルの問題が原因でエラーが発生します。これは、プロパティがまだ入力されていないので、予期されています。

1. ファイルを起動してFlash Access Manager AIRアプリケーションをイ [!DNL .air] ンストールします（AIR 1.5以降が必要）。
1. Flash Access Manager AIRアプリケーションを起動します。

   サーバーが以外の場所で実行されている場合は、ア [*!DNL https:// localhost:8080*]プリケーションがサーバーに接続できないことを示すエラーが表示されます。 エラーダイアログを閉じ、「環境設定」タブでPackagerサーバーのURLに正しいURLを入力します。 サーバーが指定したURLで実行され、プロパティーファイルがクラスパスにある場合、「環境設定」画面にプロパティーファイルの値が入力されます。 PackagerサーバーのURLを設定すると、AIRアプリケーションはこの設定を記憶するので、次回アプリケーションを起動したときにこの設定を入力する必要はありません。
1. 「環境設定」タブの値を入力し、をクリックしま **[!UICONTROL Save]**&#x200B;す。
1. 監視フォルダーを使用する場合は、手順3で見つけたエラーを回復するために、サーバーを再起動する必要があります。 環境設定が正しく設定されている場合は、起動時にエラーは表示されません。


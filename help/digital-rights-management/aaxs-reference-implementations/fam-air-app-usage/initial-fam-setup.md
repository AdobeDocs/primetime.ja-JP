---
title: Flash Accessマネージャの初期セットアップ
description: Flash Accessマネージャの初期セットアップ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# 初期Flash Accessマネージャのセットアップ{#initial-flash-access-manager-setup}

Flash Accessマネージャを設定するには、次の手順を実行します。

1. Packagerサーバーをデプロイします。 このサーバーは、ファイアウォール内のユーザーのみが使用できます（このソフトウェアをパブリック側のコンピューターに展開しないでください）。 サーバーの展開について詳しくは、[ライセンスサーバーと監視フォルダーパッケージャーの展開](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md)を参照してください。

   * [!DNL flashaccess-packager.war]をTomcatのWebappsフォルダにコピーします。
   * リソースからクラスパス上の場所に[!DNL flashaccess-refimpl-packager.properties]をコピーします。
   * サーバーの開始。 プロパティファイルの問題が原因でエラーが発生します。これは、プロパティがまだ入力されていないために期待されます。

1. [!DNL .air]ファイルを起動して、Flash AccessマネージャーAIRアプリケーションをインストールします（AIR 1.5以降が必要）。
1. Flash AccessマネージャーAIRアプリケーションを起動します。

   `https://localhost:8080*`以外の場所でサーバーが実行されている場合は、アプリケーションがサーバーに接続できないことを示すエラーが表示されます。 エラーダイアログを閉じて、「環境設定」タブでPackager Server URLの正しいURLを入力します。 サーバーが指定したURLで実行され、プロパティーファイルがクラスパス上にある場合、「環境設定」画面にプロパティーファイルの値が入力されます。 PackagerサーバーのURLを設定すると、AIRアプリケーションはこの設定を記憶するので、次回アプリケーションを起動したときにこの設定を入力する必要はありません。
1. 「環境設定」タブの値を入力し、「**[!UICONTROL Save]**」をクリックします。
1. 監視フォルダーを使用する場合は、サーバーを再起動して、手順3で確認したエラーを回復する必要があります。 環境設定が正しく設定されている場合は、起動中にエラーは表示されません。


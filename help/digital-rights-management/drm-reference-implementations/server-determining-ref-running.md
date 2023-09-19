---
title: 参照実装ライセンスサーバーが正しく実行されているかどうかの判断
description: 参照実装ライセンスサーバーが正しく実行されているかどうかの判断
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# 参照実装ライセンスサーバーが正しく実行されているかどうかの判断 {#determining-if-reference-implementation-license-server-runs-properly}

参照実装ライセンスサーバーが正しく起動したかどうかを判断する方法はいくつかあります。 次の項目を表示すると、 [!DNL catalina.log] ライセンスサーバは独自のログファイルにログを記録するので、ログでは不十分な場合があります。 以下の手順に従って、参照実装が正しく開始されていることを確認します。

* 以下を確認します。 [!DNL AdobeFlashAccess.log] ファイル。 リファレンス実装がログ情報を書き込む場所です。 このログファイルの場所は、 [!DNL log4j.xml] ファイルに保存し、任意の場所を指すように変更できます。 デフォルトでは、ログファイルは catalina を実行する作業ディレクトリにコピーされます。

* 次の URL に移動します。 [!DNL https:// flashaccess/license/v4]*サーバ：サーバポート*. 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツのセグメントをパッケージ化し、サンプルビデオプレーヤーを設定してから再生することです。

このプロセスについて、以下の手順で説明します。

1. 次に移動： [!DNL \Reference Implementation\Command Line Tools] フォルダー。

   詳しくは、 [コマンドラインツールのインストール](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) コマンドラインツールのインストール方法を参照してください。

1. 次のコマンドを入力して、単純な匿名 DRM ポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   詳しくは、 [コマンドラインの使用](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) DRM ポリシーマネージャーを使用して DRM ポリシーを作成する方法に関する情報です。

1. を設定します。 `encrypt.license.serverurl` プロパティを [!DNL flashaccesstools.properties] ファイルをライセンスサーバーの URL に追加します。

   例： [!DNL https:// localhost:8080/]. The [!DNL flashaccesstools.properties] ファイルは [!DNL \Reference Implementation\Command Line Tools] フォルダー。

1. 次のコマンドを入力して、コンテンツのセグメントをパッケージ化します。

```
       java -jar libs\AdobePackager.jar  
       <i class="+ topic ph hi-d="" i "="">
         test_input_FLV  
        <i class="+ topic ph hi-d="" i "="">
       output_file  
               -p policy_test.pol 
       </i class="+ topic> 
       </i class="+ topic>
```

1. 生成された 2 つのファイルを [!DNL webapps\ROOT\Content] Tomcat サーバー上のフォルダー。
1. 次に移動： [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] ディレクトリにコピーし、次の場所にコンテンツをコピーします。 [!DNL webapps\ROOT\SVP\] Tomcat サーバー上のフォルダー。

1. Flash Playerバージョン 10.1 以降をインストールします。
1. Web ブラウザーを開き、次の URL に移動します。 [!DNL        https:// localhost:8080/SVP/player.html]

1. 次の URL に移動し、 **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. ビデオの再生に失敗した場合は、エラーコードがサンプルビデオプレーヤーのログパネルに表示されているか、エラーコードが [!DNL AdobeFlashAccess.log] ファイル。

   これで、 [!DNL AdobeFlashAccess.log] log4j.xml ファイル内のログファイルを編集し、変更します。 デフォルトでは、ログファイルは catalina を実行する作業ディレクトリにコピーされます。

---
title: 参照実装ライセンスサーバーが正しく動作しているかどうかの確認
description: 参照実装ライセンスサーバーが正しく動作しているかどうかの確認
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 参照実装ライセンスサーバーが正しく動作しているかどうかの確認 {#determining-if-reference-implementation-license-server-is-running-properly}

サーバーが正しく起動したかどうかを判断する方法はいくつかあります。 の表示 [!DNL catalina.log] ライセンスサーバは独自のログファイルにログを記録するので、ログでは不十分な場合があります。 以下の手順に従って、参照実装が正しく開始されていることを確認します。

* 以下を確認します。 [!DNL AdobeFlashAccess.log] ファイル。 リファレンス実装がログ情報を書き込む場所です。 このログファイルの場所は、 [!DNL log4j.xml] ファイルに保存し、任意の場所を指すように変更できます。 デフォルトでは、ログファイルは、catalina を実行した作業ディレクトリに出力されます。

* 次の URL に移動します。 `https:///flashaccess/license/v4<your server:server port>`. 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツの一部をパッケージ化し、サンプルビデオプレーヤーを設定して再生することです。 このプロセスについて、以下の手順で説明します。

1. 次に移動： [!DNL \Reference Implementation\Command Line Tools] フォルダー。 コマンドラインツールのインストールについては、 [コマンドラインツールのインストール](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. 次のコマンドを使用して、単純な匿名ポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Policy Manager を使用してポリシーを作成する方法の詳細については、「 [コマンドラインの使用](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. を設定します。 `encrypt.license.serverurl` プロパティを [!DNL flashaccesstools.properties] ファイルをライセンスサーバーの URL に追加します ( 例： `https:// localhost:8080/`) をクリックします。 The [!DNL flashaccesstools.properties] ファイルは、 [!DNL \Reference Implementation\Command Line Tools] フォルダー。

1. 次のコマンドを使用して、コンテンツをパッケージ化します。

   ```java
       java -jar libs\AdobePackager.jar  
   <i class="+ topic ph hi-d="" i "="">
   test_input_FLV  
   <i class="+ topic ph hi-d="" i "="">
   output_file  
               -p policy_test.pol 
   </i class="+ topic> 
   </i class="+ topic>
   ```

1. 生成された 2 つのファイルを Tomcat にコピーします。 [!DNL webapps\ROOT\Content] フォルダー。
1. に移動します。 `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` をクリックし、Tomcat にコンテンツをコピーします。 `webapps\ROOT\SVP\` フォルダー。
1. Flash Player10.1 以降をインストールします。
1. Web ブラウザーを開き、次の URL に移動します。

   `https:// localhost:8080/SVP/player.html`
1. 次の URL に移動し、再生ボタンをクリックします。

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. ビデオの再生に失敗した場合は、サンプルビデオプレーヤーのログパネルまたは `AdobeFlashAccess.log` ファイル。 の場所 `AdobeFlashAccess.log` ログファイルは、log4j.xml ファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、ログファイルは catalina を実行した作業ディレクトリに書き込まれます。

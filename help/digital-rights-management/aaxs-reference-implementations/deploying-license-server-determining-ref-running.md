---
description: 'null'
seo-description: 'null'
seo-title: 参照実装ライセンスサーバーが正しく実行されているかどうかの確認
title: 参照実装ライセンスサーバーが正しく実行されているかどうかの確認
uuid: 84d32c94-7594-464e-a883-5338b52de2bf
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# リファレンス実装ライセンスサーバーが正しく実行されているかどうかを確認しています{#determining-if-reference-implementation-license-server-is-running-properly}

サーバーが正しく起動したかどうかを判断する方法はいくつかあります。 [!DNL catalina.log]ログを表示するだけでは不十分な場合があります。ライセンスサーバーは独自のログファイルにログを記録します。 次の手順に従って、リファレンスの実装が正しく起動していることを確認します。

* [!DNL AdobeFlashAccess.log]ファイルを確認します。 これは、リファレンスの実装によるログ情報の書き込み先です。 このログファイルの場所は[!DNL log4j.xml]ファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、カタリナを実行した作業ディレクトリにログファイルが出力されます。

* 次のURLに移動します。`https:///flashaccess/license/v4<your server:server port>`. 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツの一部をパッケージ化し、サンプルビデオプレーヤーを設定して再生することです。 次の手順で、このプロセスを説明します。

1. [!DNL \Reference Implementation\Command Line Tools]フォルダーに移動します。 コマンドラインツールのインストールについては、[コマンドラインツールのインストール](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools)を参照してください。

1. 次のコマンドを使用して、単純な匿名ポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Policy Managerを使用したポリシーの作成について詳しくは、「[コマンドラインの使用](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md)」を参照してください。

1. [!DNL flashaccesstools.properties]ファイルの`encrypt.license.serverurl`プロパティをライセンスサーバーのURLに設定します（例：`https:// localhost:8080/`）。 [!DNL flashaccesstools.properties]ファイルは[!DNL \Reference Implementation\Command Line Tools]フォルダーの下にあります。

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

1. 生成された2つのファイルをTomcat [!DNL webapps\ROOT\Content]フォルダにコピーします。
1. `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release`に移動し、Tomcat `webapps\ROOT\SVP\`フォルダに内容をコピーします。
1. Flash Player10.1以降をインストールします。
1. Webブラウザーを開き、次のURLに移動します。

   `https:// localhost:8080/SVP/player.html`
1. 次のURLに移動し、「再生」ボタンをクリックします。

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. ビデオの再生に失敗した場合は、エラーコードがサンプルビデオプレーヤーのログペインまたは`AdobeFlashAccess.log`ファイルに書き込まれているかどうかを確認します。 `AdobeFlashAccess.log`ログファイルの場所はlog4j.xmlファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、カタリナを実行した作業ディレクトリにログファイルが書き込まれます。

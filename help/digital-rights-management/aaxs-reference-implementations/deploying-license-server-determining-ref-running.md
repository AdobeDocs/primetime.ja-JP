---
description: 'null'
seo-description: 'null'
seo-title: 参照実装ライセンスサーバーが正しく実行されているかどうかの確認
title: 参照実装ライセンスサーバーが正しく実行されているかどうかの確認
uuid: 84d32c94-7594-464e-a883-5338b52de2bf
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# 参照実装ライセンスサーバーが正しく実行されているかどうかの確認 {#determining-if-reference-implementation-license-server-is-running-properly}

サーバーが正しく起動しているかどうかを判断する方法はいくつかあります。 ライセンスサ [!DNL catalina.log] ーバーは独自のログファイルにログを記録するので、ログを表示するだけでは不十分な場合があります。 次の手順に従って、リファレンスの実装が正しく開始されていることを確認します。

* ファイルを確認 [!DNL AdobeFlashAccess.log] します。 リファレンスの実装では、ログ情報が書き込まれます。 このログファイルの場所は、ファイルによって示さ [!DNL log4j.xml] れ、任意の場所を指すように変更することができます。 デフォルトでは、ログファイルはcatalinaを実行した作業ディレクトリに出力されます。

* 次のURLに移動します。 `https:///flashaccess/license/v4<your server:server port>`. 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツの一部をパッケージ化し、サンプルビデオプレーヤーを設定して再生する方法です。 次の手順で、このプロセスを説明します。

1. フォルダーに移動 [!DNL \Reference Implementation\Command Line Tools] します。 コマンドラインツールのインストールについて詳しくは、「コマンドラ [インツールのインストール」を参照してくださ](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools)い。

1. 次のコマンドを使用して、単純な匿名ポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Policy Managerを使用したポリシーの作成について詳しくは、「コマンドラインの使用 [方法」を参照してくださ](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md)い。

1. ファイル `encrypt.license.serverurl` 内のプロパティ [!DNL flashaccesstools.properties] をライセンスサーバーのURL(例： `https:// localhost:8080/`)に設定します。 ファイ [!DNL flashaccesstools.properties] ルはフォルダの下にあ [!DNL \Reference Implementation\Command Line Tools] ります。

1. 次のコマンドを使用して、コンテンツの一部をパッケージ化します。

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

1. 生成された2つのファイルをTomcatフォルダにコピー [!DNL webapps\ROOT\Content] します。
1. に移動し、Tomcat `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` フォルダにその内容をコピー `webapps\ROOT\SVP\` します。
1. Flash Player 10.1以降をインストールします。
1. Webブラウザーを開き、次のURLに移動します。

   `https:// localhost:8080/SVP/player.html`
1. 次のURLに移動し、「再生」ボタンをクリックします。

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. ビデオの再生に失敗した場合は、サンプルビデオプレーヤーのログペインまたはファイルにエラーコードが書き込まれているかどうかを確認し `AdobeFlashAccess.log` ます。 ログファイルの場 `AdobeFlashAccess.log` 所はlog4j.xmlファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、ログファイルはcatalinaを実行した作業ディレクトリに書き込まれます。

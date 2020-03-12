---
description: 'null'
seo-description: 'null'
seo-title: 参照実装ライセンスサーバーが正しく実行されるかどうかの判断
title: 参照実装ライセンスサーバーが正しく実行されるかどうかの判断
uuid: afd82d6d-a11c-48ff-b48c-8f81d4b406a0
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# 参照実装ライセンスサーバーが正しく実行されるかどうかの判断 {#determining-if-reference-implementation-license-server-runs-properly}

リファレンス実装ライセンスサーバーが正しく起動しているかどうかを判断する方法はいくつかあります。 ライセンスサーバー [!DNL catalina.log] が独自のログファイルにログを記録するので、ログを表示するだけでは不十分である可能性があります。 次の手順に従って、リファレンスの実装が正しく開始されていることを確認します。

* ファイルを確認 [!DNL AdobeFlashAccess.log] します。 リファレンスの実装では、ログ情報が書き込まれます。 このログファイルの場所は、ファイルによって示さ [!DNL log4j.xml] れ、任意の場所を指すように変更することができます。 デフォルトでは、ログファイルはcatalinaを実行する作業ディレクトリにコピーされます。

* 次のURLに移動します。サー [!DNL https:// flashaccess/license/v4]*バー：サーバーポート&#x200B;*。 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツのセグメントをパッケージ化し、サンプルビデオプレーヤーを設定してから再生する方法です。

次の手順で、このプロセスを説明します。

1. フォルダに移動 [!DNL \Reference Implementation\Command Line Tools] します。

   コマンドラ [インツールのインストール方法については](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) 、「コマンドラインツールのインストール」を参照してください。

1. 次のコマンドを入力して、単純な匿名DRMポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   DRMポリシ [ーマネージャーを使用して](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) 、DRMポリシーを作成する方法については、「コマンドラインの使用」を参照してください。

1. ファイル内 `encrypt.license.serverurl` のプロパティ [!DNL flashaccesstools.properties] をライセンスサーバーのURLに設定します。

   For example, [!DNL https:// localhost:8080/]. ファイ [!DNL flashaccesstools.properties] ルはフォルダー内にあ [!DNL \Reference Implementation\Command Line Tools] ります。

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

1. 生成された2つのファイルをTomcatサー [!DNL webapps\ROOT\Content] バー上のフォルダにコピーします。
1. ディレクトリ [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] に移動し、Tomcatサーバー上の[!DNL webapps\ROOT\SVP\]フォルダに内容をコピーします。

1. Flash Playerバージョン10.1以降をインストールします。
1. Webブラウザーを開き、次のURLに移動します。 [!DNL        https:// localhost:8080/SVP/player.html]

1. 次のURLに移動し、をクリックしま **[!UICONTROL Play]**&#x200B;す。 [!DNL https:// localhost:8080/Content/]*`your_encrypted_FLV`*.

1. ビデオの再生に失敗した場合は、エラーコードがサンプルビデオプレーヤーのログペインに表示されているか、ファイルに追加されているかを確認し [!DNL AdobeFlashAccess.log] ます。

   log4j.xmlファイル内のログファ [!DNL AdobeFlashAccess.log] イルの場所を検索し、変更できるようになりました。 デフォルトでは、ログファイルはcatalinaを実行する作業ディレクトリにコピーされます。


---
description: 'null'
seo-description: 'null'
seo-title: 参照実装のライセンスサーバーが正しく実行されるかどうかを確認する
title: 参照実装のライセンスサーバーが正しく実行されるかどうかを確認する
uuid: afd82d6d-a11c-48ff-b48c-8f81d4b406a0
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# 参照実装ライセンスサーバーが正しく実行されるかどうかを判断する{#determining-if-reference-implementation-license-server-runs-properly}

リファレンス実装ライセンスサーバーが正しく起動したかどうかを判断するには、いくつかの方法があります。 [!DNL catalina.log]ログは、ライセンスサーバーが独自のログファイルにログするので、表示できない場合があります。 次の手順に従って、リファレンスの実装が正しく起動していることを確認します。

* [!DNL AdobeFlashAccess.log]ファイルを確認します。 これは、リファレンスの実装によるログ情報の書き込み先です。 このログファイルの場所は[!DNL log4j.xml]ファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、ログファイルはcatalinaを実行する作業ディレクトリにコピーされます。

* 次のURLに移動します。[!DNL https:// flashaccess/license/v4]*サーバー：サーバーポート*。 「License Server is setup correctly」というテキストが表示されます。

サーバーが正しく動作しているかどうかをテストする別の方法は、テストコンテンツのセグメントをパッケージ化し、サンプルビデオプレーヤーを設定してから再生することです。

次の手順で、このプロセスを説明します。

1. [!DNL \Reference Implementation\Command Line Tools]フォルダーに移動します。

   コマンドラインツールのインストール方法については、[コマンドラインツールのインストール](../drm-reference-implementations/command-line-tools/install-command-line-tools.md)を参照してください。

1. 次のコマンドを入力して、単純な匿名DRMポリシーを作成します。

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   DRMポリシーマネージャーでDRMポリシーを作成する方法については、[コマンドラインの使用](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md)を参照してください。

1. [!DNL flashaccesstools.properties]ファイルの`encrypt.license.serverurl`プロパティをライセンスサーバーのURLに設定します。

   例：[!DNL https:// localhost:8080/]。 [!DNL flashaccesstools.properties]ファイルは[!DNL \Reference Implementation\Command Line Tools]フォルダーにあります。

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

1. 生成された2つのファイルをTomcatサーバーの[!DNL webapps\ROOT\Content]フォルダにコピーします。
1. [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release]ディレクトリに移動し、Tomcatサーバーの [!DNL webapps\ROOT\SVP\] フォルダーに内容をコピーします。

1. Flash Playerバージョン10.1以降をインストールします。
1. Webブラウザーを開き、次のURLに移動します。[!DNL        https:// localhost:8080/SVP/player.html]

1. 次のURLに移動し、**[!UICONTROL Play]**&#x200B;をクリックします。[!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*。

1. ビデオの再生に失敗した場合は、サンプルビデオプレーヤーのログペインにエラーコードが表示されているか、または[!DNL AdobeFlashAccess.log]ファイルに追加されているかを確認します。

   これで、log4j.xmlファイル内の[!DNL AdobeFlashAccess.log]ログファイルの場所を検索し、それを変更できます。 デフォルトでは、ログファイルはcatalinaを実行する作業ディレクトリにコピーされます。


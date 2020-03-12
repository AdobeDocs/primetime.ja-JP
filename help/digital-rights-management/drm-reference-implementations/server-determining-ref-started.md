---
description: 'null'
seo-description: 'null'
seo-title: ライセンスサーバーが正しく起動しているかどうかを確認する
title: ライセンスサーバーが正しく起動しているかどうかを確認する
uuid: a6a034c9-b3c4-4e26-b901-d2c132c00c52
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# ライセンスサーバーが正しく起動しているかどうかを確認する {#check-whether-the-license-server-started-properly}

リファレンス実装ライセンスサーバーが正しく起動しているかどうかを判断する方法はいくつかあります。 1つの方法はログをチェックするこ [!DNL catalina.log] とですが、ライセンスサーバーが独自のログファイルにログを記録するので、これでは不十分な場合があります。
1. ファイルを確認 [!DNL AdobeFlashAccess.log] します。

   リファレンス実装ライセンスサーバーがログ情報を書き込む場所です。 このログファイルの場所は、ファイルによって示さ [!DNL log4j.xml] れ、任意の場所を指すように変更できます。 デフォルトでは、ログファイルは `catalina` Tomcatスクリプトを実行する作業ディレクトリにコピーされます。
1. 次のURLに移動し、「License Server is setup correctly」というテキストが表示されることを確認します。
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

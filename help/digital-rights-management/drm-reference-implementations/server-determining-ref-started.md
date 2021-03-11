---
title: ライセンスサーバーが正しく起動したかどうかを確認します。
description: ライセンスサーバーが正しく起動したかどうかを確認します。
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# ライセンスサーバーが正しく起動したかどうかを確認{#check-whether-the-license-server-started-properly}

リファレンス実装ライセンスサーバーが正しく起動したかどうかを判断するには、いくつかの方法があります。 1つの方法は[!DNL catalina.log]ログを調べることですが、ライセンスサーバは独自のログファイルにログするので、これでは十分ではないかもしれません。
1. [!DNL AdobeFlashAccess.log]ファイルを確認します。

   これは、リファレンスの実装のライセンスサーバーがログ情報を書き込む場所です。 このログファイルの場所は[!DNL log4j.xml]ファイルで示され、任意の場所を指すように変更できます。 デフォルトでは、`catalina` Tomcatスクリプトを実行する作業ディレクトリにログファイルがコピーされます。
1. 次のURLに移動し、「License Server is setup correcty」というテキストが表示されることを確認します。
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

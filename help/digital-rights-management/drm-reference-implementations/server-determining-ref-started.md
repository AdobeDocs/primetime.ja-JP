---
title: ライセンスサーバーが正しく起動したかどうかを確認します。
description: ライセンスサーバーが正しく起動したかどうかを確認します。
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# ライセンスサーバーが正しく起動したかどうかを確認します。 {#check-whether-the-license-server-started-properly}

参照実装ライセンスサーバーが正しく起動したかどうかを判断する方法はいくつかあります。 1 つの方法は、 [!DNL catalina.log] ログに書き込まれますが、ライセンスサーバが独自のログファイルにログを記録するので、これでは不十分な場合があります。
1. 以下を確認します。 [!DNL AdobeFlashAccess.log] ファイル。

   Reference Implementation ライセンスサーバーがログ情報を書き込む場所です。 このログファイルの場所は、 [!DNL log4j.xml] ファイルに含まれ、任意の場所を指すように変更できます。 デフォルトでは、ログファイルは、 `catalina` Tomcat スクリプト。
1. 次の URL に移動し、「License Server is setup correctly」というテキストが表示されることを確認します。
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

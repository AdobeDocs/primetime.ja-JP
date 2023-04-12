---
title: 付録 B「デバッグのヒント」
description: 付録 B「デバッグのヒント」
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# 付録 B:デバッグのヒント {#appendix-b-debugging-tips}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。


## 一時データをクリア中 {#clearing-temporary-data}

Adobe Primetime認証は、一時データ（ブラウザーキャッシュ、LSO キャッシュ、cookie など）を格納します。 テスト時に新しいスレートが得られるように、一時データをクリアすることが重要です。

- [ブラウザーのキャッシュと cookie のクリア](#clearing-the-browser-cache-and-cookies)
- [LSO キャッシュのクリア](#clearing-lsos-cache)\
    

## ブラウザーのキャッシュと cookie のクリア {#clearing-the-browser-cache-and-cookies}

ブラウザーは信頼できますが、Firefox では次のようになります。&quot;ツール&quot; -\> &quot;最近の履歴をクリア。.&quot; -\> &quot;クリアする時間範囲：&quot;で&quot;すべて&quot;を選択します。「詳細」では「Cookies」と「Cache」をチェックし、「今すぐクリア」をクリックします。\
 

## LSO キャッシュのクリア {#clearing-lsos-cache}

次にアクセス： [Flash Playerヘルプ](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html).

を選択します。 ```entitlement.\*``` （テストの内容に応じて）、「web サイトを削除」をクリックします。\
 

## デバッグツール {#tools}

Adobe Primetime認証エンジニアは、次のデバッグツールを使用します。

- Firebug - <http://www.getfirebug.com/>
- Flashbug（Flash Player のデバッグバージョンで動作） <https://addons.mozilla.org/en-US/firefox/addon/14465/>
- ライブ HTTP ヘッダー — <https://addons.mozilla.org/en-US/firefox/addon/3829/>
- Fiddler - <http://www.fiddler2.com/fiddler2/>
- Charles - <http://www.charlesproxy.com/>
- Wireshark - <http://www.wireshark.org/>


<!--
## Related Information

- [Programmer Integration Guide](/help/authentication/programmer-integration-guide-overview.md)

- [Using Charles Proxy (Tech Note)](https://tve.zendesk.com/hc/en-us/articles/204962849-Using-Charles-Proxy)
-->
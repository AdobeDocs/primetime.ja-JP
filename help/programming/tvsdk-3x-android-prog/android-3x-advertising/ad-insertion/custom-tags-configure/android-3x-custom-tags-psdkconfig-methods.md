---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: b75aebac-4b94-4c42-bed4-3c17ad989cd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# タグ{#config-class-methods-for-tags}のConfigクラスメソッド

MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。

TVSDKは、ストリーム固有の設定を指定していないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` カスタムタグを管理するには、次のメソッドを公開します。

**特定のカスタムタグのサブスクライブ**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | サブスクライブされたタグの現在のリストを取得します。 |
| `public final void setSubscribedTags(String[] tags);` | アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。  アプリケーションは、`setAdTags`を通じて送信されるすべてのタグも自動的にサブスクライブします。 |

**デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getAdTags;` | 広告タグの現在のリストを取得します。 |
| `public final void setAdTags(String[] tags);` | デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 |

次の点に注意してください。

* setterメソッドでは、タグパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKは`IllegalArgumentException`をスローします。
* カスタムタグ名には、`#`プレフィックスを含める必要があります。

   例えば、`#EXT-X-ASSET`は正しいカスタムタグ名ですが、`EXT-X-ASSET`は正しくありません。

* メディアストリームの読み込み後は、設定を変更できません。
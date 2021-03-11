---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。
title: タグのConfigクラスメソッド
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '184'
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
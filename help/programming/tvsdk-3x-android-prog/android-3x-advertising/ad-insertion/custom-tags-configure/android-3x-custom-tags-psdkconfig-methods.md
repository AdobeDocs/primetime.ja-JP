---
description: MediaPlayerItemConfig クラスを使用して、 TVSDK 内でカスタムタグ名をグローバルに設定できます。
title: タグの Config クラスメソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# タグの Config クラスメソッド {#config-class-methods-for-tags}

MediaPlayerItemConfig クラスを使用して、 TVSDK 内でカスタムタグ名をグローバルに設定できます。

TVSDK は、ストリーム固有の設定を指定しないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` は、カスタムタグを管理する次のメソッドを公開しています。

**特定のカスタムタグを購読する**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | サブスクライブ済みタグの現在のリストを取得します。 |
| `public final void setSubscribedTags(String[] tags);` | アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。  また、アプリケーションは、 `setAdTags`. |

**デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getAdTags;` | 広告タグの現在のリストを取得します。 |
| `public final void setAdTags(String[] tags);` | デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 |

次の点に注意してください。

* setter メソッドでは、タグパラメーターに null 値を含めることはできません。

  検出された場合、 TVSDK は `IllegalArgumentException`.
* カスタムタグ名には、 `#` プレフィックス。

  例： `#EXT-X-ASSET` は正しいカスタムタグ名ですが、 `EXT-X-ASSET` が正しくありません。

* メディアストリームの読み込み後は、設定を変更できません。

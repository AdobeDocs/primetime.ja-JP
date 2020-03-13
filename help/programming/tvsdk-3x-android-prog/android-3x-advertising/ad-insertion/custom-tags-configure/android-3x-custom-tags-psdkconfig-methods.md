---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: b75aebac-4b94-4c42-bed4-3c17ad989cd1
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# タグのConfigクラスメソッド {#config-class-methods-for-tags}

MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。

TVSDKは、ストリーム固有の設定を指定しないメディアストリームに、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` 次のメソッドを使用して、カスタムタグを管理します。

**特定のカスタムタグのサブスクライブ**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | サブスクライブされたタグの現在のリストを取得します。 |
| `public final void setSubscribedTags(String[] tags);` | アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。  また、アプリケーションは、送信されたすべてのタグを自動的にサブスクライブしま `setAdTags`す。 |

**デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ**

| <b>メソッド</b> | <b>説明</b> |
|--- |--- |
| `public final String[] getAdTags;` | 広告タグの現在のリストを取得します。 |
| `public final void setAdTags(String[] tags);` | デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 |

次の点に注意してください。

* setterメソッドでは、tagsパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKはIDをスローしま `IllegalArgumentException`す。
* カスタムタグ名に接頭辞を含める必要が `#` あります。

   例えば、は正し `#EXT-X-ASSET` いカスタムタグ名ですが、正しくあ `EXT-X-ASSET` りません。

* メディアストリームの読み込み後は、設定を変更できません。
---
description: PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-description: PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 1d3651a0-3b70-4d3a-8ced-663a9dad7205
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# タグのConfigクラスメソッド{#config-class-methods-for-tags}

PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定しないメディアストリームに対して、グローバル設定を自動的に適用します。

`PTSDKConfig` 次のメソッドを使用して、カスタムタグを管理します。

| **特定のカスタムタグのサブスクライブ** |
|---|
| `subscribedTags` | サブスクライブされたタグの現在のリストを取得します。 |
| `setSubscribedTags` | アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 |
| **デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ** |
| `adTags` | 広告タグの現在のリストを取得します。 |
| `setAdTags` | デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 |

次の点に注意してください。

* setterメソッドでは、tagsパラメーターにnull値を含めることはできません。
* カスタムタグ名には、#プレフィックスを含める必要があります。

   例えば、#EXT-X-ASSETは正しいカスタムタグ名ですが、EXT-X-ASSETは正しくありません。
* メディアストリームの読み込み後は、設定を変更できません。


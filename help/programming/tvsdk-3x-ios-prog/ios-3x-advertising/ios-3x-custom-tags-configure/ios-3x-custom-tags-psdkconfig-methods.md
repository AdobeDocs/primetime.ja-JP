---
description: PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-description: PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 27f1df0a-bbd3-4d80-820e-b659f2f33069
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# タグ{#config-class-methods-for-tags}のConfigクラスメソッド

PTSDKConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定していないメディアストリームに対して、グローバル設定を自動的に適用します。

`PTSDKConfig` カスタムタグを管理するには、次のメソッドを公開します。

| **特定のカスタムタグのサブスクライブ** |  |
|---|---|
| `subscribedTags` | サブスクライブされたタグの現在のリストを取得します。 |
| `setSubscribedTags` | アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 |
| **デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ** |
| `adTags` | 広告タグの現在のリストを取得します。 |
| `setAdTags` | デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 |


次の点に注意してください。

* setterメソッドでは、タグパラメーターにnull値を含めることはできません。
* カスタムタグ名にはプレフィックス#を含める必要があります。

   例えば、#EXT-X-ASSETは正しいカスタムタグ名ですが、EXT-X-ASSETは正しくありません。
* メディアストリームの読み込み後は、設定を変更できません。
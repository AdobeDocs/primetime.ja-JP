---
description: ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張が含まれていないストリームの再生をサポートしています。
seo-description: ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張が含まれていないストリームの再生をサポートしています。
seo-title: 拡張なしストリーム
title: 拡張なしストリーム
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 拡張なしストリーム{#extensionless-streams}

ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張が含まれていないストリームの再生をサポートしています。

## フラグメントレベル {#section_0E035129501D4A77BBC14192D8A53A86}

ブラウザーTVSDKは、応答の最初の数バイトを解析し、拡張なしのフラグメントのコンテンツタイプを検出します。 有効なコンテンツタイプが検出されなかった場合、ブラウザーTVSDKはエラーをスローします。

## マニフェストレベル {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

ブラウザーTVSDKは、メソッド `mediaResource.resourceType` で渡されたパラメーターを使用し `replaceCurrentResource` て、マニフェストURLのコンテンツタイプを検出します。 詳しくは、クラスを参照してく `AdobePSDK.MediaPlayer` ださい。

UIフレームワークプレーヤーでは、次のようにメディアリソースのリソースタイプを指定できます。

```js
var playerWrapper = ptp.videoPlayer('.videoDiv', { 
  player: { 
    mediaResource: { 
      resourceUrl:'Specify Resource Url', 
      resourceType: ‘Specify Resource Type. Refer AdobePSDK.MediaResourceType' 
    } 
  } 
}); 
```

を指定 `resourceType` しない場合、UIフレームワークはリソースURL拡張からリソースの種類を決定し、その後メソッドに渡 `replaceCurrentResource` します。

>[!TIP]
>
>拡張子のないマニフェストの場合、UIフレ `resourceType` ームワークでリソースを読み込む際には、が常に渡されることを確認します。


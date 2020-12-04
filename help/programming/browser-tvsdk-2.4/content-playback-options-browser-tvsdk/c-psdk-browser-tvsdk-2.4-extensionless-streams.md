---
description: ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張子が含まれないストリームの再生をサポートしています。
seo-description: ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張子が含まれないストリームの再生をサポートしています。
seo-title: Extensionless streams
title: Extensionless streams
uuid: c69ba62b-a940-4211-920d-2e559849fd6d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Extensionless streams{#extensionless-streams}

ブラウザーTVSDKは、現在、マニフェストとフラグメントに拡張子が含まれないストリームの再生をサポートしています。

## フラグメントレベル{#section_0E035129501D4A77BBC14192D8A53A86}

ブラウザーTVSDKは、応答の最初の数バイトを解析して、拡張なしのフラグメントのコンテンツタイプを検出します。 有効なコンテンツタイプが検出されなかった場合、Browser TVSDKはエラーをスローします。

## マニフェストレベル{#section_AAD9EBAC883D4CC3A0133A45B555EECF}

ブラウザーTVSDKは、`replaceCurrentResource`メソッドで渡された`mediaResource.resourceType`パラメーターを使用して、マニフェストURLのコンテンツタイプを検出します。 詳しくは、`AdobePSDK.MediaPlayer`クラスを参照してください。

UIフレームワークプレイヤーでは、メディアリソースのリソースの種類を次のように指定できます。

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

`resourceType`を指定しない場合、UIフレームワークはリソースURL拡張からリソースの種類を決定し、`replaceCurrentResource`メソッドに渡します。

>[!TIP]
>
>拡張子を持たないマニフェストの場合は、UIフレームワークでリソースを読み込むときに、必ず`resourceType`が渡されるようにします。


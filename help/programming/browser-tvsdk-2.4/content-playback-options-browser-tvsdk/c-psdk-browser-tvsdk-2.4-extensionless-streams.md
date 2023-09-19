---
description: ブラウザー TVSDK は、現在、マニフェストとフラグメントに拡張機能が含まれていないストリームの再生をサポートしています。
title: 拡張機能のないストリーム
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# 拡張機能のないストリーム{#extensionless-streams}

ブラウザー TVSDK は、現在、マニフェストとフラグメントに拡張機能が含まれていないストリームの再生をサポートしています。

## フラグメントレベル {#section_0E035129501D4A77BBC14192D8A53A86}

ブラウザー TVSDK は、応答の最初の数バイトを解析して、拡張機能のないフラグメントのコンテンツタイプを検出します。 有効なコンテンツタイプが検出されなかった場合、Browser TVSDK はエラーをスローします。

## マニフェストレベル {#section_AAD9EBAC883D4CC3A0133A45B555EECF}

ブラウザー TVSDK は、 `mediaResource.resourceType` に渡されるパラメーター `replaceCurrentResource` マニフェスト URL のコンテンツタイプを検出するためのメソッド。 詳しくは、 `AdobePSDK.MediaPlayer` クラス。

UI Framework Player では、メディアリソースのリソースタイプを次のように指定できます。

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

次の場合 `resourceType` が指定されていない場合、UI Framework は、リソース URL 拡張からリソースタイプを決定し、次にに渡されます。 `replaceCurrentResource` メソッド。

>[!TIP]
>
>拡張機能がないマニフェストの場合は、 `resourceType` は、UI フレームワークでリソースを読み込む際に常に渡されます。

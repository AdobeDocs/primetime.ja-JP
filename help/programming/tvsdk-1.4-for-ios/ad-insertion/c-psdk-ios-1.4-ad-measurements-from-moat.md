---
description: TVSDK は、FreeWheel や VAST 応答を提供する他の adserver から情報を取得します。 FreeWheel は、VAST 応答内で、Mort サービスからの情報を提供します。 Mort のサービスは、クリエイティブが観客の利益を捉えたり無視したりすることをより正確に示す、広告インプレッションを数えます。
title: 堀からの広告の測定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 堀からの広告の測定{#ad-measurements-from-moat}

TVSDK は、FreeWheel や VAST 応答を提供する他の adserver から情報を取得します。 FreeWheel は、VAST 応答内で、Mort サービスからの情報を提供します。 Mort のサービスは、クリエイティブが観客の利益を捉えたり無視したりすることをより正確に示す、広告インプレッションを数えます。

Mort は、ブラウザーからアプリケーション内まで、多くの用途にわたって広く測定・閲覧を行うサービスです。 Mort は、複数のプラットフォームにわたって、リアルタイムでマーケティング分析データを生成します。

VAST 応答 XML には、プロパティと、コードが読み取ることのできる要素、最も外側の広告 id プロパティ、最も外側の拡張要素が含まれています。 どちらの場合でも、 TVSDK を使用して、広告 ID 情報と拡張情報の両方を保存し、情報をツリー構造に整理できます。 この組織では、コードは任意のレベルからデータを取得し、必要な場所に渡すことができます。 最も外側にある広告 id プロパティの値により、コードで関連するキャンペーンの情報を調整できます。

例えば、FreeWheel は Extensions 要素でデータを返すことができます。 以下に、サンプル要素を示します。

```xml
<Extensions> 
   <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
     <MeasurementInfo renditionID="6398737" type="MediaFile"> 
      <MoatID> 
       <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
       <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID> 
        <![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]]]> 
        <![CDATA[> 
        </MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions>
```

Freewheel は、以下のサンプルに示すように、Ad 要素で id プロパティを設定することもできます。

```
<Ad id="118566" sequence="1">
```

クラスについては、 API ドキュメントを参照してください `PTNetworkAdInfo` in `PTAdAsset`.

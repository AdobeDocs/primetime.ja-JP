---
description: TVSDKは、FreeWheelやVAST応答を提供する他のサーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえたり無視したりするクリエイティブをより正確に示すため、広告インプレッション数を数えます。
seo-description: TVSDKは、FreeWheelやVAST応答を提供する他のサーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえたり無視したりするクリエイティブをより正確に示すため、広告インプレッション数を数えます。
seo-title: 堀からの広告測定
title: 堀からの広告測定
uuid: 76fa9ca0-58bd-44fe-82ce-72fdf6fcc28c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# 堀からの広告測定{#ad-measurements-from-moat}

TVSDKは、FreeWheelやVAST応答を提供する他のサーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえたり無視したりするクリエイティブをより正確に示すため、広告インプレッション数を数えます。

Mortは、ブラウザーからアプリケーション内まで、様々な用途にわたって広告を測定し、閲覧するサービスです。 Marutは、複数のプラットフォームにわたってリアルタイムでマーケティング分析データを生成します。

VAST応答XMLには、プロパティとコードが読み取れる要素、最も外側の広告idプロパティ、最も外側の拡張要素が含まれます。 どちらの方法でも、コードはTVSDKを使用して、広告ID情報と拡張情報の両方を保存し、情報をツリー構造で整理できます。 この組織では、任意のレベルのデータを取得し、必要な場所にコードを渡すことができます。 最も外側の広告idプロパティの値により、コードは関連するキャンペーンからの情報を調整できます。

例えば、FreeWheelはExtensions要素でデータを返すことができます。 以下に、要素の例を示します。

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

Freewheelは、次のサンプルに示すように、Ad要素でidプロパティを設定することもできます。

```
<Ad id="118566" sequence="1">
```

`PTAdAsset`内のクラス`PTNetworkAdInfo`のAPIドキュメントを参照してください。

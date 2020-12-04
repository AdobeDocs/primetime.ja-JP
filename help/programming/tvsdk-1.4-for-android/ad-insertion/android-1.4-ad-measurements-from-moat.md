---
description: TVSDKは、FreeWheelや、VASTレスポンスを提供する他の広告サーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえるか無視するかをより正確に示すため、広告インプレッション数を数えます。
seo-description: TVSDKは、FreeWheelや、VASTレスポンスを提供する他の広告サーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえるか無視するかをより正確に示すため、広告インプレッション数を数えます。
seo-title: 堀からの広告測定
title: 堀からの広告測定
uuid: 73ef3a14-7ad6-4e67-8ad3-eabbeb898a09
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# 堀からの広告測定{#ad-measurements-from-moat}

TVSDKは、FreeWheelや、VASTレスポンスを提供する他の広告サーバーから情報を取得します。 FreeWheelはVAST応答内でMorthサービスから情報を提供します。 Mortuサービスは、オーディエンスの利益を捕らえるか無視するかをより正確に示すため、広告インプレッション数を数えます。

Mortは、ブラウザーからアプリケーション内まで、様々な用途にわたって広告を測定し、閲覧するサービスです。 Marutは、複数のプラットフォームにわたってリアルタイムでマーケティング分析データを生成します。

VAST応答XMLには、プロパティとコードで読み取れる要素、最も外側の`Ad id`プロパティ、最も外側の`Extension`要素が含まれます。 どちらの方法でも、コードはTVSDKを使用して`Ad id`情報と`Extension`情報の両方を保存し、情報をツリー構造に編成できます。 この組織では、任意のレベルのデータを取得し、必要な場所にコードを渡すことができます。 最も外側の`Ad id`プロパティの値を使用すると、コードは関連付けられたキャンペーンからの情報を調整できます。

例えば、FreeWheelはExtensions要素でデータを返すことができます。 以下に、要素の例を示します。

```xml
<?xml version="1.0"?> 
<Extensions> 
  <Extension type="FreeWheel"> 
    <Parameter name="moat"> 
      <MeasurementInfo renditionID="6398737" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
      <MeasurementInfo renditionID="6398739" type="MediaFile"> 
        <MoatID><![CDATA[169843;56705;17860255;17860316;2509639;g8912342;103311138;g436558;530633]]></MoatID> 
      </MeasurementInfo> 
    </Parameter> 
  </Extension> 
</Extensions> 
```

フリーホイールでは、次の例に示すように、`Ad`要素に`id`プロパティを設定することもできます。

```xml
<Ad id="118566" sequence="1">
```

クラス`NetworkAdInfo`のAPIドキュメントを参照してください。

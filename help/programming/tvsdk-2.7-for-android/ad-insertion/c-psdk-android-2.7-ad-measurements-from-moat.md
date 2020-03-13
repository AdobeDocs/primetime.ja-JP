---
description: TVSDKは、FreeWheelや他の広告サーバーから情報を取得し、VAST応答を提供します。 FreeWheelはVAST応答内で、Morthサービスの情報を提供します。 Morthサービスは、クリエイティブが観客の利益を捕らえるか、無視するかをより正確に示すため、広告インプレッション数をカウントします。
seo-description: TVSDKは、FreeWheelや他の広告サーバーから情報を取得し、VAST応答を提供します。 FreeWheelはVAST応答内で、Morthサービスの情報を提供します。 Morthサービスは、クリエイティブが観客の利益を捕らえるか、無視するかをより正確に示すため、広告インプレッション数をカウントします。
seo-title: 堀からの広告測定
title: 堀からの広告測定
uuid: b89f900f-50ab-4152-9c0f-11f82d92bffa
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 堀からの広告測定{#ad-measurements-from-moat}

TVSDKは、FreeWheelや他の広告サーバーから情報を取得し、VAST応答を提供します。 FreeWheelはVAST応答内で、Morthサービスの情報を提供します。 Morthサービスは、クリエイティブが観客の利益を捕らえるか、無視するかをより正確に示すため、広告インプレッション数をカウントします。

Morthは、ブラウザーからアプリケーション内まで、様々な用途で広く測定および閲覧するサービスです。 Martigは、複数のプラットフォームにわたってリアルタイムでマーケティング分析データを生成します。

VAST応答XMLには、プロパティと、コードで読み取ることのできる要素、最も外側のプロパ `Ad id` ティ、最も外側の要素が含ま `Extension` れます。 どちらの方法でも、TVSDKを使用して情報と情報の両方を保 `Ad id` 存し、 `Extension` 情報をツリー構造で整理することができます。 この組織では、任意のレベルのデータを取得し、必要な場所にデータを渡すことができます。 最も外側のプロパティの値を使 `Ad id` 用すると、コードで関連するキャンペーンの情報を調整できます。

例えば、FreeWheelは拡張要素でデータを返すことができます。 以下に、サンプル要素を示します。

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

フリーホイールは、次の例のよ `id` うに、要素 `Ad` 内でプロパティを設定することもできます。

```xml
<Ad id="118566" sequence="1">
```

API情報については、NetworkAdInfoクラスのAPIドキュメントを参照してくだ [さい](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/)

---
description: TVSDK は、FreeWheel や、VAST 応答を提供する他の広告サーバーから情報を取得します。 FreeWheel は、VAST 応答内で、Mort サービスからの情報を提供します。 Mort のサービスは、クリエイティブが観客の利益を捉えるか無視するかをより正確に示す正確な情報とインプレッションを数えます。
title: 堀からの広告の測定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# 堀からの広告の測定{#ad-measurements-from-moat}

TVSDK は、FreeWheel や、VAST 応答を提供する他の広告サーバーから情報を取得します。 FreeWheel は、VAST 応答内で、Mort サービスからの情報を提供します。 Mort のサービスは、クリエイティブが観客の利益を捉えるか無視するかをより正確に示す正確な情報とインプレッションを数えます。

Mort は、ブラウザーからアプリケーション内まで、多くの用途にわたって広く測定・閲覧を行うサービスです。 Mort は、複数のプラットフォームにわたって、リアルタイムでマーケティング分析データを生成します。

VAST 応答 XML には、プロパティと、コードが読み取れる要素が含まれ、最も外側に `Ad id` プロパティと最も外側の `Extension` 要素を選択します。 どちらの方法でも、 TVSDK を使用して、 `Ad id` 情報と `Extension` 情報をツリー構造に整理します。 この組織では、コードは任意のレベルからデータを取得し、必要な場所に渡すことができます。 最も外側の `Ad id` プロパティを使用すると、コードで関連するキャンペーンの情報を調整できます。

例えば、FreeWheel は Extensions 要素でデータを返すことができます。 以下に、サンプル要素を示します。

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

Freewheel は、 `id` プロパティを `Ad` 要素を作成します。

```xml
<Ad id="118566" sequence="1">
```

クラスについては、 API ドキュメントを参照してください `NetworkAdInfo`.

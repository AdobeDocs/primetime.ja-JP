---
description: 'null'
seo-description: 'null'
seo-title: 堀からの広告測定
title: 堀からの広告測定
uuid: a29c1e74-df15-47d2-9bd6-1d366c5cdf37
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 堀からの広告測定 {#ad-measurement-from-moat}

TVSDKは、FreeWheelおよびVAST応答を提供する他のサーバーから情報を取得します。 FreeWheelはVAST応答内で、Morthサービスの情報を提供します。 Morthサービスは、クリエイティブが観客の利益を捕らえたり無視したりすることをより正確に示すため、広告インプレッション数をカウントします。

Morthは、ブラウザーからアプリケーション内まで、様々な用途で広く測定および閲覧するサービスです。 Martigは、複数のプラットフォームにわたってリアルタイムでマーケティング分析データを生成します。

VAST応答XMLには、プロパティと、コードで読み取ることのできる要素、最も外側の広告IDプロパティ、最も外側の拡張要素が含まれます。 どちらの方法でも、TVSDKを使用して、広告ID情報と拡張情報の両方を保存し、情報をツリー構造で整理できます。 この組織では、任意のレベルのデータを取得し、必要な場所にデータを渡すことができます。 最も外側の広告IDプロパティの値を使用すると、コードで関連するキャンペーンの情報を調整できます。

例えば、FreeWheelは拡張要素でデータを返すことができます。 以下に、サンプル要素を示します。

```
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

Freewheelは、以下の例に示すように、Ad要素でidプロパティを設定することもできます。

```
<Ad id="118566" sequence="1">
```

AdobePSDK.NetworkAdInfoクラスについては、APIドキュメントを参照してください。

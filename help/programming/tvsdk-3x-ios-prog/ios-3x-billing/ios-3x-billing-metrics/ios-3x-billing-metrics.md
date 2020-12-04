---
description: 実際の使用量に関係なく固定率ではなく、使用した分のみの支払いを希望する顧客に対応するために、Adobeは使用状況指標を収集し、これらの指標を使用して顧客の請求額を決定します。
seo-description: 実際の使用量に関係なく固定率ではなく、使用した分のみの支払いを希望する顧客に対応するために、Adobeは使用状況指標を収集し、これらの指標を使用して顧客の請求額を決定します。
seo-title: 課金の使用状況指標
title: 課金の使用状況指標
uuid: e792cc72-b1ae-42ce-8b71-f9f9f1de0614
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# 請求指標{#billing-metrics}

実際の使用量に関係なく固定率ではなく、使用した分のみの支払いを希望する顧客に対応するために、Adobeは使用状況指標を収集し、これらの指標を使用して顧客の請求額を決定します。

プレイヤーがストリーム開始イベントを生成するたびに、TVSDK開始がHTTPメッセージを定期的にAdobeの請求システムに送信します。 請求可能期間と呼ばれる期間は、標準のVOD、プロVOD（ミッドロール広告が有効）、ライブコンテンツで異なる場合があります。 各コンテンツタイプのデフォルトの期間は30分ですが、実際の値はAdobeとの契約によって決まります。

メッセージには次の情報が含まれます。

* コンテンツタイプ（ライブ、リニアまたはVOD）
* コンテンツURL
* 広告が有効かどうか
* ミッドロール広告が有効かどうか（VODのみ）
* ストリームがDRMで保護されているかどうか
* TVSDKのバージョンとプラットフォーム

Adobeはこの設定を事前に構成していますが、設定を変更する場合は、Adobe有効化担当者にご相談ください。

TVSDKがAdobeに送信する統計を監視するには、Adobe有効化担当者からURLを取得し、Charlesなどのネットワークキャプチャツールを使用してデータを表示します。

## 請求指標の設定{#configure-billing-metrics}

デフォルト設定を使用する場合は、課金を有効にしたり設定したりする必要はありません。 Adobe有効化担当者から別の設定パラメーターを取得した場合は、PTBillingMetricsConfigurationクラスを使用して、メディアプレイヤーを初期化する前にこれらのパラメーターを設定します。

ほとんどのお客様は、デフォルトの設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレイヤーの使用期間中有効です。 メディアプレイヤーを初期化した後は、設定を変更できません。

請求指標を設定するには：

次のコードサンプルを入力します。

```
PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
billingConfig.enabled = YES; 
billingConfig.stdVODBillableDurationMinutes = 60.0; 
billingConfig.proVODBillableDurationMinutes = 30.0; 
billingConfig.liveBillableDurationMinutes = 15.0; 
                
// metadata is the PTMetadata instance set on PTMediaPlayerItem 
[metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
```

## 請求指標を送信{#transmit-billing-metrics}

TVSDKは、請求指標をXML形式でAdobeに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

TVSDKがAdobeに送信する統計情報を監視するためにネットワークキャプチャツールを使用する場合は、次のようなユニットが表示されます。

```
<request> 
     <sc_xml_ver>1.0</sc_xml_ver> 
     <reportSuiteID>ptebilling</reportSuiteID> 
     <visitorID>5536C629-5EF7-4F02-8E5D-9FA136CB3CED</visitorID> 
     <pageName>com.adobe.primetime.psdksample</pageName> 
     <timestamp>2016-11-22T18:06:30+0000</timestamp> 
     <userAgent>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</userAgent> 
     <contextData> 
         <billingMetrics> 
                 <contentDuration>1799111</contentDuration> 
                 <contentURL>https%3A%2F%2Fdevimages.apple.com.edgekey.net%2Fstreaming%2Fexamples%2Fbipbop_16x9%2Fbipbop_16x9_variant.m3u8</contentURL> 
                 <contentType>vod</contentType> 
                 <midrollEnabled>true</midrollEnabled> 
                 <tvsdkVersion>1.0.211</tvsdkVersion> 
                 <platform>Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Mobile/13B143</platform> 
                 <publisherID>com.adobe.primetime.psdksample</publisherID> 
                 <adsEnabled>true</adsEnabled> 
                 <type>start</type> 
         </billingMetrics> 
     </contextData> 
</request>
```

ブール値のプロパティ`drmProtected`、`adsEnabled`、および`midrollEnabled`は、trueの場合にのみ表示されます。
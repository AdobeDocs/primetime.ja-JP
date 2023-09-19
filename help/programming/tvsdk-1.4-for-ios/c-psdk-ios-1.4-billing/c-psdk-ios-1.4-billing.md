---
description: 実際の使用状況に関係なく、固定料金ではなく、使用した分のみを支払いたい場合に対応するために、Adobeは使用状況指標を収集し、これらの指標を使用して顧客に対する請求額を決定します。
title: 請求指標
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# 請求指標 {#billing-metrics}

実際の使用状況に関係なく、固定料金ではなく、使用した分のみを支払いたい場合に対応するために、Adobeは使用状況指標を収集し、これらの指標を使用して顧客に対する請求額を決定します。

プレーヤーがストリーム開始イベントを生成するたびに、 TVSDK は HTTP メッセージを定期的にAdobeの請求システムに送信し始めます。 この期間（課金可能な期間と呼ばれる）は、標準の VOD、Pro VOD（ミッドロール広告が有効な場合）、ライブコンテンツで異なる場合があります。 各コンテンツタイプのデフォルトの期間は 30 分ですが、実際の値はAdobeとの契約によって決まります。

メッセージには、次の情報が含まれます。

* コンテンツタイプ（ライブ、リニア、VOD）
* コンテンツ URL
* 広告が有効かどうか
* ミッドロール広告が有効かどうか（VOD のみ）
* ストリームが DRM で保護されているかどうか
* TVSDK のバージョンとプラットフォーム

Adobeはこの設定を事前に行いますが、設定を変更する場合は、Adobeイネーブルメント担当者にお問い合わせください。

TVSDK がAdobeに送信する統計を監視するには、Adobeイネーブルメント担当者から URL を取得し、Charles などのネットワークキャプチャツールを使用してデータを確認します。

## 請求指標の設定 {#configure-billing-metrics}

デフォルトの設定を使用する場合、課金を有効にしたり設定したりするために必要な操作は他にありません。 Adobeイネーブルメント担当者から異なる設定パラメーターを取得した場合は、 PTBillingMetricsConfiguration クラスを使用して、メディアプレーヤーを初期化する前にこれらのパラメーターを設定します。

ほとんどのお客様は、デフォルト設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレーヤーの存続期間中も有効です。 メディアプレーヤーを初期化した後は、設定を変更できません。

請求指標を設定するには、次の手順に従います。

1. 次のコードサンプルを入力します。

   ```
   PTBillingMetricsConfiguration *billingConfig = [[[PTBillingMetricsConfiguration alloc] init] autorelease]; 
   billingConfig.enabled = YES; 
   billingConfig.stdVODBillableDurationMinutes = 60.0; 
   billingConfig.proVODBillableDurationMinutes = 30.0; 
   billingConfig.liveBillableDurationMinutes = 15.0; 
   
   // metadata is the PTMetadata instance set on PTMediaPlayerItem 
   [metadata setMetadata:billingConfig forKey:PTBillingMetricsConfigurationMetadataKey];
   ```

## 請求指標の送信 {#transmit-billing-metrics}

TVSDK は、請求指標を XML 形式でAdobeに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

TVSDK がAdobeに送信する統計を監視するためにネットワークキャプチャツールを使用する場合、次のような単位が表示されます。

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

boolean プロパティ `drmProtected`, `adsEnabled`、および `midrollEnabled` 真の場合にのみ表示されます。

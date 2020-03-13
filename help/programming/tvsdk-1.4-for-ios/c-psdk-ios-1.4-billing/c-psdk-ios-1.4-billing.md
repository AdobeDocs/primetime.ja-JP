---
description: 実際の使用に関係なく、使用した分のみの支払いを行いたい顧客に対応するために、アドビでは使用状況指標を収集し、これらの指標を使用して顧客に対する請求額を決定します。
seo-description: 実際の使用に関係なく、使用した分のみの支払いを行いたい顧客に対応するために、アドビでは使用状況指標を収集し、これらの指標を使用して顧客に対する請求額を決定します。
seo-title: 請求指標
title: 請求指標
uuid: 658ffbcd-dedc-464c-8ec7-aa3bdfcb1512
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 請求指標 {#billing-metrics}

実際の使用に関係なく、使用した分のみの支払いを行いたい顧客に対応するために、アドビでは使用状況指標を収集し、これらの指標を使用して顧客に対する請求額を決定します。

プレイヤーがストリーム開始イベントを生成するたびに、TVSDKはHTTPメッセージを定期的にアドビの課金システムに送信し始めます。 請求可能期間と呼ばれる期間は、標準のVOD、プロVOD（ミッドロール広告が有効）およびライブコンテンツで異なる場合があります。 各コンテンツタイプのデフォルトの期間は30分ですが、実際の値はアドビとの契約によって決まります。

メッセージには次の情報が含まれます。

* コンテンツタイプ（ライブ、リニアまたはVOD）
* コンテンツURL
* 広告が有効かどうか
* ミッドロール広告が有効かどうか（VODのみ）
* ストリームがDRMで保護されているかどうか
* TVSDKのバージョンとプラットフォーム

アドビはこの配置を事前に設定しますが、配置を変更する場合は、アドビの有効化担当者にお問い合わせください。

TVSDKがアドビに送信する統計を監視するには、アドビの有効化担当者からURLを取得し、Charlesなどのネットワークキャプチャツールを使用してデータを表示します。

## 請求指標の設定 {#configure-billing-metrics}

デフォルトの設定を使用する場合、課金を有効にしたり設定したりするために必要な操作は他にありません。 アドビの有効化担当者から別の設定パラメーターを取得した場合は、PTBillingMetricsConfigurationクラスを使用して、メディアプレイヤーを初期化する前にこれらのパラメーターを設定します。

ほとんどのお客様は、デフォルトの設定を使用する必要があります。

>[!IMPORTANT]
>
>設定した設定は、メディアプレイヤーの使用期間中有効のままになります。 メディアプレイヤーを初期化した後は、設定を変更できません。

請求指標を設定するには：

1. 次のコード例を入力します。

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

TVSDKは、請求指標をXML形式でアドビに送信します。

<!--<a id="example_13ABDB1CC0B549968A534765378DA3A0"></a>-->

ネットワークキャプチャツールを使用してTVSDKがアドビに送信する統計を監視する場合、次のようなユニットが表示されます。

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

Booleanプロパティ、お `drmProtected`よび `adsEnabled`Trueの `midrollEnabled` 場合にのみ表示されます。
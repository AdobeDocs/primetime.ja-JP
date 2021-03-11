---
description: このMulti-DRMワークフローでは、WidevineおよびPlayReadyで暗号化されたDASHコンテンツのセットアップ、パッケージ化、ライセンス、再生を行います。
title: WidevineおよびPlayReady用のMulti-DRMワークフロー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# WidevineおよびPlayReady用のMulti-DRMワークフロー{#multi-drm-workflow-for-widevine-and-playready}

このMulti-DRMワークフローでは、WidevineおよびPlayReadyで暗号化されたDASHコンテンツのセットアップ、パッケージ化、ライセンス、再生を行います。

Primetime TVSDKは、Widevineで暗号化またはPlayReady暗号化されたDASHコンテンツのHTML5およびAndroidでの再生をTVSDKバージョン2.Xでのみサポートしています。DASHコンテンツの暗号化はCommon Encryption仕様で定義され、詳細は本ドキュメントの範囲外です。 ここでは、DASH形式と暗号化の仕様に関する詳細、およびサポートされるコンテンツの生成に使用できるツールの一部について説明します。

>[!NOTE]
>
>Widevineで暗号化されたDASHコンテンツの再生時にAndroid TVSDK 1.Xにバックポートする予定はありません。

## DASHコンテンツと共通の暗号化の概要{#section_33A881158F724835B4B89AAE97302B17}

ダッシュコンテンツは、再生するビデオおよびオーディオファイルを指すxml形式のメインマニフェストで構成されます。 以下の例では、DASHマニフェストは、マニフェストのURLに対するビデオURL video/1080_30.mp4を指し、オーディオURL audio/1080_30.mp4を指しています。

```
<MPD xmlns="urn:mpeg:DASH:schema:MPD:2011" xmlns:cenc="urn:mpeg:cenc:2013" xmlns:scte35="urn:scte:scte35:2013" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"mediaPresentationDuration="PT30S" minBufferTime="PT8S" profiles="urn:mpeg:dash:profile:isoff-on-demand:2011" type="static" xsi:schemaLocation="urn:mpeg:DASH:schema:MPD:2011 DASH-MPD.xsd">
    <Period id="1" start="PT0S">
        <AdaptationSet bitstreamSwitching="true" contentType="video" id="1" segmentAlignment="true" startWithSAP="2">
            <Representation bandwidth="4215100" codecs="avc1.4d4029" height="1080" id="1" mimeType="video/mp4" width="1920">
                <BaseURL>video/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
 
        <AdaptationSet bitstreamSwitching="true" contentType="audio" id="2" segmentAlignment="1" startWithSAP="1">
            <Representation bandwidth="320600" codecs="mp4a.40.02" id="1" mimeType="audio/mp4">
                <BaseURL>audio/1080_30.mp4</BaseURL>
                <CueInfo schemeIdUri="urn:adobe:mpeg:dash:cueinfo:2012"/>
            </Representation>
        </AdaptationSet>
    </Period>
</MPD>
```

以下に、共通暗号化が適用されたマニフェストの例を示します。 マニフェスト内のWidevineコンテンツ保護XML要素（`<ContentProtection>`ブロック）には、base64エンコードされたpssh（保護システム固有のヘッダー）ボックスが含まれています。 psshボックスには、コンテンツの復号化を初期化するために必要なデータが含まれます。 このデータは、マニフェストが参照するビデオ/オーディオコンテンツにも埋め込まれます。 DASHコンテンツには、PlayReadyの場合は1、Widevineの場合は1など、複数のコンテンツ保護要素を含めることができます。

```
<?xml version="1.0" ?>
<MPD mediaPresentationDuration="PT3M35.533S" minBufferTime="PT15.00S" profiles="urn:mpeg:dash:profile:isoff-live:2011" type="static" xmlns="urn:mpeg:dash:schema:mpd:2011" xmlns:cenc="urn:mpeg:cenc:2013">
  <!-- Created with Bento4 mp4-dash.py, VERSION=1.6.0-607 -->
  <Period>
    <!-- Audio -->
    <AdaptationSet mimeType="audio/mp4" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
      <Representation audioSamplingRate="44100" bandwidth="200429" codecs="mp4a.40.2" id="audio/und">
        <AudioChannelConfiguration schemeIdUri="urn:mpeg:dash:23003:3:audio_channel_configuration:2011" value="2"/>
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="audio/und/init.mp4"/>
          <SegmentURL media="audio/und/seg-1.m4f"/>
          <SegmentURL media="audio/und/seg-2.m4f"/>
          <SegmentURL media="audio/und/seg-3.m4f"/>
          <SegmentURL media="audio/und/seg-4.m4f"/>
          <SegmentURL media="audio/und/seg-5.m4f"/>
          <SegmentURL media="audio/und/seg-6.m4f"/>
          <SegmentURL media="audio/und/seg-7.m4f"/>
          <SegmentURL media="audio/und/seg-8.m4f"/>
          <SegmentURL media="audio/und/seg-9.m4f"/>
          <SegmentURL media="audio/und/seg-10.m4f"/>
          <SegmentURL media="audio/und/seg-11.m4f"/>
          <SegmentURL media="audio/und/seg-12.m4f"/>
          <SegmentURL media="audio/und/seg-13.m4f"/>
          <SegmentURL media="audio/und/seg-14.m4f"/>
          <SegmentURL media="audio/und/seg-15.m4f"/>
          <SegmentURL media="audio/und/seg-16.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
 
    <!-- Video -->
    <AdaptationSet maxHeight="720" maxWidth="1280" mimeType="video/mp4" minHeight="720" minWidth="1280" segmentAlignment="true" startWithSAP="1">
      <!-- Common Encryption -->
      <ContentProtection cenc:default_KID="9e828b37-842d-9f71-0233-c007fb1d4f5b" schemeIdUri="urn:mpeg:dash:mp4protection:2011" value="cenc"/>
      <!-- Widevine -->
      <ContentProtection schemeIdUri="urn:uuid:edef8ba9-79d6-4ace-a3c8-27dcd51d21ed">
        <cenc:pssh>
        AAAAQ3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAACMIARIQnoKLN4Qtn3ECM8AH+x1PWxoKaW50ZXJ0cnVzdCIBKg==
        </cenc:pssh>
      </ContentProtection>
 
      <Representation bandwidth="2640920" codecs="avc1.64001F" frameRate="30" height="720" id="video/1" scanType="progressive" width="1280">
        <SegmentList duration="15000" timescale="1000">
          <Initialization sourceURL="video/1/init.mp4"/>
          <SegmentURL media="video/1/seg-1.m4f"/>
          <SegmentURL media="video/1/seg-2.m4f"/>
          <SegmentURL media="video/1/seg-3.m4f"/>
          <SegmentURL media="video/1/seg-4.m4f"/>
          <SegmentURL media="video/1/seg-5.m4f"/>
          <SegmentURL media="video/1/seg-6.m4f"/>
          <SegmentURL media="video/1/seg-7.m4f"/>
          <SegmentURL media="video/1/seg-8.m4f"/>
          <SegmentURL media="video/1/seg-9.m4f"/>
          <SegmentURL media="video/1/seg-10.m4f"/>
          <SegmentURL media="video/1/seg-11.m4f"/>
          <SegmentURL media="video/1/seg-12.m4f"/>
          <SegmentURL media="video/1/seg-13.m4f"/>
          <SegmentURL media="video/1/seg-14.m4f"/>
          <SegmentURL media="video/1/seg-15.m4f"/>
        </SegmentList>
      </Representation>
    </AdaptationSet>
  </Period>
</MPD>
```

上の最初の例では各ストリームに対して1つのファイルのみを参照し、2つ目の例では一連の小さなコンテンツのフラグメントを参照しています。 フラグメントを明示的に参照する代わりに、次のようにフラグメントテンプレートを定義することもできます。

```
<Representation bandwidth="348000" codecs="avc1.42c01e" height="360" id="1" width="640">
    <BaseURL>video/</BaseURL>
    <SegmentTemplate initialization="JaigoInit.mp4" media="Jaigo$Number$.m4s" startNumber="0" timescale="1000">
        <SegmentTimeline>
            <S d="4538" t="0"/>
            <S d="4304" t="4538"/>
            <S d="4004" t="8842"/>
            <S d="2102" t="12846"/>
        </SegmentTimeline>
    </SegmentTemplate>
</Representation>
```

この場合、コンテンツパーサー(TVSDK)は、Jaigo0.m4s、Jaigo1.m4s、Jaigo2.m4sなどでビデオコンテンツを見つけることを期待しています。 これは主にライブストリーミングに使用され、クライアントが時々マニフェストを再度ダウンロードする必要がないという利点があります。

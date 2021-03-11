---
description: マニフェストサーバは、提案されたHTTPライブストリーミング標準に準拠したM3U8形式のマスター再生リストを返します。 TS（バリアントトランスポートストリーム）のセットで構成され、各TSには、異なるビットレートとフォーマットに対する同じコンテンツのレンディションが含まれます。 Adobe Primetime広告挿入は、クライアントビデオプレーヤーが解釈するEXT-X-MARKERディレクティブタグを追加します。
title: EXT-X-MARKER指令
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---


# EXT-X-MARKERディレクティブ{#ext-x-marker-directive}

マニフェストサーバは、提案されたHTTPライブストリーミング標準に準拠したM3U8形式のマスター再生リストを返します。 TS（バリアントトランスポートストリーム）のセットで構成され、各TSには、異なるビットレートとフォーマットに対する同じコンテンツのレンディションが含まれます。 Adobe Primetime広告挿入は、クライアントビデオプレーヤーが解釈するEXT-X-MARKERディレクティブタグを追加します。

EXT-X-MARKERタグについて詳しくは、[Adobe PrimetimeHTTPライブストリーミングプロファイル](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf)を参照してください。

>[!NOTE]
>
>この機能は、ブートストラップマニフェストサーバーのURLに`pttrackingmode`パラメーターが含まれていない場合にのみ使用できます。

>[!NOTE]
>
>EXT-X-MARKERタグは、コンテンツセグメントではなく、広告セグメントに追加されます。

[HTTPライブストリーミング](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23)のドラフト規格では、バリアント再生リストの内容と形式が記述されています。 EXT-X-MARKERタグは、コールバックを呼び出すようクライアントに指示します。 これには、次のコンポーネントが含まれます。

* **プログラムストリームのコンテキスト内での、このコールバックイベントの** IDUnique identifier（文字列）。

* **callbackイベントの** TYPEType（文字列）:PodBegin、PodEnd、PrerollPodBegin、PrerollPodEnd、またはAdBegin

* **デ** ィレクティブが有効なままの、タグを含むセグメントの開始からの時間（秒）。

* **オフ** ィショナル。コールバックを呼び出す必要がある場合の、セグメント再生の開始を基準としたオフセット（秒）。

   * `PodBegin` とは、DATA属性にビーコン情報が `PrerollPodBegin` 含まれ、セグメントの開始時に呼び出されます。そのため、`OFFSET`タグはここでは使用できません。

   * `AdBegin` には、DATA属性にビーコン情報が含まれ、そのセグメントの開始時にインプレッションタグが呼び出されます。`OFFSET`タグはここでも使用できません。

   * `PodEnd` とは、DATA属性にビーコン情報が `PrerollPodEnd` 含まれますが、現在のセグメントの最後に呼び出されます。これらのタグは、ポッド内の最後の広告の最後のセグメントの最後に呼び出されると見なされるからです。この場合、`OFFSET`は`<duration of segment>`に設定され、現在のセグメントの最後にビーコンが起動されることを指定します。

* **コールバック呼び出し時にアプリケーションに渡すデータを含む、重複引用符で囲まれた** DATABase64エンコードされた文字列。VMAP1.0およびVAST3.0仕様に準拠する広告トラッキング情報が含まれます。

* **** COUNT広告の時間に繋ぎ合わされる広告の数。

   TYPEコンポーネントがPodBeginまたはPrerollPodBeginに設定されている場合にのみ適用可能です。

* **** BREAKDURT入力された広告の時間の合計時間（秒）。

   TYPEコンポーネントがPodBeginまたはPrerollPodBeginに設定されている場合にのみ適用可能です。

コールバックを構築する際に、EXT-X-MARKERコンポーネントを次のように解釈します。

* タグに`OFFSET`が含まれる場合は、そのセグメント内のコンテンツ再生の開始を基準に、指定されたオフセットでコールバックを実行します。 それ以外の場合は、セグメント開始のコンテンツの再生と同時にコールバックを実行します。
* `DURATION`を使用して、広告コンテンツの進行状況を追跡したり、イベントを追跡するためのURLをリクエストしたりします。
* コールバックに`ID`、`TYPE`、および`DATA`を渡します。

`PrerollPodBegin`と`PrerollPodEnd`の値(`TYPE`)を使用して、ライブ/リニアストリームで最初に再生するTSセグメントを決定します。

>[!NOTE]
>
>`PrerollPodBegin`および`PrerollPodEnd`の値は、プリロール広告がライブストリームに挿入されている場合にのみ使用できます。

マニフェストサーバーには、次のセグメントにEXT-X-MARKERタグが含まれています。

* 広告の時間の最初のセグメントで、広告ポッドの開始を追跡します。
* 広告ポッド内の個々の広告の開始、完了、進行状況を追跡するための、広告の最初のセグメント。
* 広告の時間の最後のセグメント。広告ポッドの終わりを追跡するために使用します。

マニフェストサーバーは、各広告ブレークの開始と終了を追跡するための`VMAP1.0-conformant` XMLドキュメントを送信します。 これは、広告サーバーから返される実際のVMAP1.0応答のフィルタリングされたバージョンで、主に以下に示すようにトラッキングイベントが含まれます。

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<vmap:VMAP xmlns:vmap="https://www.iab.net/vmap-1.0" version="1.0"> 
    <vmap:AdBreak breakType="linear" breakId="mypre" timeOffset="start"> 
        <vmap:TrackingEvents> 
            <vmap:Tracking event="breakStart"> 
                https://MyServer.com/breakstart.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="breakEnd"> 
                https://MyServer.com/breakend.gif 
            </vmap:Tracking> 
            <vmap:Tracking event="error"> 
                https://MyServer.com/error.gif 
            </vmap:Tracking> 
        </vmap:TrackingEvents> 
    </vmap:AdBreak> 
</vmap:VMAP> 
</AdTrackingFragment> 
</AdTrackingFragments>
```

マニフェストサーバーがプログラムコンテンツに挿入する広告クリエイティブごとに、VAST3.0に準拠したXMLドキュメントを送信して、その広告を追跡します。 各XMLドキュメントには、挿入されるリニア広告クリエイティブを説明する`<InLine>`要素、またはラッパー広告（リンクまたはリダイレクトされた広告）の場合は`<Wrapper>`要素、および関連するコンパニオン広告と拡張子が含まれます。 広告が広告ポッドの一部である場合など、VAST応答にシーケンス属性が含まれる場合、ドキュメントにはその属性が含まれます。 以下は、個々の広告を追跡するためのVAST3.0準拠のXMLドキュメントの例です。

```xml
<?xml version="1.0"?> 
<AdTrackingFragments> 
<AdTrackingFragment> 
<VAST xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"  
      version="3.0"  
      xsi:noNamespaceSchemaLocation="https://service.videoplaza.com/schema/iab/vast-3.0.xsd"> 
<Ad id="903395"> 
    <InLine> 
      <AdSystem version="1.0">Auditude</AdSystem> 
      <AdTitle/> 
      <Error>https://ad.qa.auditude.com/adserver/?ErrAd1=[ERRORCODE]</Error> 
      <Impression id="urn:aeid:903395">https://ad.qa.auditude.com/adserver/e?type=adimp&amp; 
                 cid=127860991&amp; 
                 z=50183&amp; 
                 a=903395&amp; 
                 s=ef8c51dc&amp; 
                 t=1355309735&amp; 
                 w=100000&amp; 
                 uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                 l=1355280906&amp; 
                 u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                 br=1&amp; 
                 sq=1&amp; 
                 pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                 ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                               ?Cashcash=[CACHEBUSTING] 
                               ?Asset=[ASSETURI] 
      </Impression> 
      <Creatives> 
        <Creative> 
          <Linear> 
            <Duration>00:00:15</Duration> 
            <TrackingEvents> 
              ... 
              <Tracking event="firstQuartile"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=25&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking>                
              <Tracking event="midpoint"> 
                https://ad.qa.auditude.com/adserver/e?type=AD_PROGRESS&amp; 
                  a=903395&amp; 
                  a1=105&amp; 
                  ref=urn:asset:903395:105&amp; 
                  unit=percent&amp; 
                  progress=50&amp; 
                  cid=127860991&amp; 
                  z=50183&amp; 
                  a=903395&amp; 
                  s=ef8c51dc&amp; 
                  t=1355309735&amp; 
                  w=100000&amp; 
                  uid=_CxLm0b1SeKD8KXco__5TQ&amp; 
                  l=1355280906&amp; 
                  u=956c3cd141086a1da44dcae8ea4ed14a&amp; 
                  br=1&amp; 
                  sq=1&amp; 
                  pod=id:1,ctype:l,ptype:p,dur:400,lot:8,cpos:1,edur:400,elot:8&amp; 
                  ax=0,0,1720,0/?ContentPosition=[CONTENTPLAYHEAD] 
                                ?Cashcash=[CACHEBUSTING] 
                                ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="firstQuartile"> 
                https://www.Tweeeen.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                       ?Cashcash=[CACHEBUSTING] 
                                       ?Asset=[ASSETURI] 
              </Tracking> 
              <Tracking event="midpoint"> 
                https://www.Fiftyyyy.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                        ?Cashcash=[CACHEBUSTING] 
                                        ?Asset=[ASSETURI] 
              </Tracking> 
              ... 
            </TrackingEvents> 
            <VideoClicks> 
              <ClickTracking> 
                https://www.MP4-Vid-ClickTrack.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                                  ?Cashcash=[CACHEBUSTING] 
                                                  ?Asset=[ASSETURI] 
              </ClickTracking> 
              <ClickThrough> 
                https://www.cnn.com/?ContentPosition=[CONTENTPLAYHEAD] 
                                   ?Cashcash=[CACHEBUSTING] 
                                   ?Asset=[ASSETURI] 
              </ClickThrough> 
              ... 
            </VideoClicks> 
            <AdParameters>campaign_id=7012</AdParameters> 
            <MediaFiles> 
              ...            
            </MediaFiles> 
          </Linear> 
        </Creative> 
        <Creative> 
          <CompanionAds> 
            <Companion id="103" width="300" height="250"> 
              <StaticResource creativeType="image/jpeg"> 
                https://ad.qa.auditude.com/adserver/c/z=50183; 
                  l=1355280906; 
                  u=956c3cd141086a1da44dcae8ea4ed14a; 
                  uid=_CxLm0b1SeKD8KXco__5TQ; 
                  cid=127860991; 
                  s=ef8c51dc; 
                  t=1355309735; 
                  br=1; 
                  sq=1; 
                  pod=id%3a1%2cctype%3al%2cptype%3ap%2cdur 
                    %3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8; 
                  ax=0%2c0%2c1720%2c0; 
                  w=100000; 
                  a=903395; 
                  a1=103/c300x250.jpeg 
              </StaticResource> 
              <CompanionClickThrough> 
                https://ad.qa.auditude.com/adserver/l/a=903395%3Ba1=103 
                  %3Ba2=1%3Bz=50183%3Bl=1355280906%3Bu=956c3cd141086a1da44dcae8ea4ed14a 
                  %3Bcid=127860991%3Bs=ef8c51dc%3Buid=_CxLm0b1SeKD8KXco__5TQ 
                  %3Bt=1355309735%3Bbr=1%3Bsq=1%3Bpod=id%3a1%2cctype%3al%2cptype 
                  %3ap%2cdur%3a400%2clot%3a8%2ccpos%3a1%2cedur%3a400%2celot%3a8 
                  %3Bax=0%2c0%2c1720%2c0 
              </CompanionClickThrough> 
              <AdParameters>campaign_id=7012</AdParameters> 
            </Companion> 
          </CompanionAds> 
        </Creative> 
        ... 
      </Creatives> 
      <Extensions> 
        <Extension type="Behavior"> 
          ... 
        </Extension> 
      </Extensions> 
    </InLine> 
  </Ad> 
  </VAST> 
</AdTrackingFragment> 
</AdTrackingFragments> 
```

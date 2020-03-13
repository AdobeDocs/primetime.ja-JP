---
description: マニフェストサーバーは、提案されたHTTPライブストリーミング標準に準拠したM3U8形式のマスター再生リストを返します。 TS（バリアントトランスポートストリーム）のセットで構成され、各TSには異なるビットレートと形式の同じコンテンツのレンディションが含まれます。 Adobe Primetimeの広告挿入により、クライアントビデオプレーヤーで解釈されるEXT-X-MARKERディレクティブタグが追加されます。
seo-description: マニフェストサーバーは、提案されたHTTPライブストリーミング標準に準拠したM3U8形式のマスター再生リストを返します。 TS（バリアントトランスポートストリーム）のセットで構成され、各TSには異なるビットレートと形式の同じコンテンツのレンディションが含まれます。 Adobe Primetimeの広告挿入により、クライアントビデオプレーヤーで解釈されるEXT-X-MARKERディレクティブタグが追加されます。
seo-title: EXT-X-MARKER指令
title: EXT-X-MARKER指令
uuid: e349bf89-b196-47b4-a362-9913fa28b2c6
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# EXT-X-MARKER指令 {#ext-x-marker-directive}

マニフェストサーバーは、提案されたHTTPライブストリーミング標準に準拠したM3U8形式のマスター再生リストを返します。 TS（バリアントトランスポートストリーム）のセットで構成され、各TSには異なるビットレートと形式の同じコンテンツのレンディションが含まれます。 Adobe Primetimeの広告挿入により、クライアントビデオプレーヤーで解釈されるEXT-X-MARKERディレクティブタグが追加されます。

EXT-X-MARKERタグについて詳しくは、 [Adobe Primetime HTTP Live Streaming Profileを参照してください](https://wwwimages2.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeHLS_April2014.pdf)。

>[!NOTE]
>
>この機能は、ブートストラップマニフェストサーバーのURLにパラメーターが含まれていない場合にのみ使用で `pttrackingmode` きます。

>[!NOTE]
>
>EXT-X-MARKERタグは、コンテンツセグメントではなく広告セグメントに追加されます。

[HTTPライブストリーミングのドラフト標準では](https://tools.ietf.org/html/draft-pantos-http-live-streaming-23) 、バリアント再生リストの内容と形式が説明されています。 EXT-X-MARKERタグは、コールバックを呼び出すようクライアントに指示します。 これには、次のコンポーネントが含まれます。

* **ID** ：プログラムストリームのコンテキスト内での、このコールバックイベントの一意の識別子（文字列）。

* **TYPE** ：コールバックイベントのタイプ（文字列）:PodBegin、PodEnd、PrerollPodBegin、PrerollPodEndまたはAdBegin

* **DURATION** ：ディレクティブが有効なままのタグを持つセグメントの開始からの時間（秒）。

* **OFFSET(オプション** )。 コールバックを呼び出す必要がある場合の、セグメント再生の開始を基準とした相対オフセット（秒）。

   * `PodBegin` とは、 `PrerollPodBegin` DATA属性にビーコン情報を含み、セグメントの開始時に呼び出されます。 タグはこ `OFFSET` こでは使用できません。

   * `AdBegin` には、DATA属性にビーコン情報が含まれ、そのセグメントの開始時にインプレッションタグが呼び出されます。 このため、こ `OFFSET` こでもタグは使用できません。

   * `PodEnd` とは、 `PrerollPodEnd` DATA属性にビーコン情報が含まれているが、現在のセグメントの最後に呼び出されるタグです。これらのタグは、ポッド内の最後の広告の最後のセグメントの最後に呼び出されると考えられるからです。 この場合、は、現在 `OFFSET` のセグメント `<duration of segment>` の最後にビーコンを起動するように設定されます。

* **DATA** Base64エンコードされた文字列で、コールバックを呼び出すときにアプリケーションに渡すデータを二重引用符で囲みます。 VMAP1.0およびVAST3.0仕様に準拠する広告トラッキング情報が含まれます。

* **COUNT** ：広告の時間に関連付けられる広告の数。

   TYPEコンポーネントがPodBeginまたはPrerollPodBeginに設定されている場合にのみ適用されます。

* **BREAKDUR** ：埋め込まれた広告の時間の合計時間（秒）。

   TYPEコンポーネントがPodBeginまたはPrerollPodBeginに設定されている場合にのみ適用されます。

コールバックを構築する際、EXT-X-MARKERコンポーネントを次のように解釈します。

* タグにが含まれる場合 `OFFSET`は、そのセグメント内のコンテンツ再生の開始を基準として、指定したオフセットでコールバックを実行します。 それ以外の場合は、そのセグメント内のコンテンツの再生が開始されるとすぐにコールバックが実行されます。
* 広告コ `DURATION` ンテンツの進行状況を追跡し、イベントを追跡するためのURLをリクエストするために使用します。
* 、お `ID`よび `TYPE`をコールバ `DATA` ックに渡します。

ライブ/リ `PrerollPodBegin`ニアストリ `PrerollPodEnd` ームで最初に `TYPE` 再生するTSセグメントを決定するには、、およびの値を使用します。

>[!NOTE]
>
>との値 `PrerollPodBegin`は、プ `PrerollPodEnd` リロール広告がライブストリームに挿入された場合にのみ使用できます。

マニフェストサーバーには、次のセグメントにEXT-X-MARKERタグが含まれます。

* 広告ポッドの開始を追跡する、広告の時間の最初のセグメント。
* 広告ポッド内の個々の広告の開始/完了/進行状況を追跡する、広告の最初のセグメント。
* 広告ポッドの終わりを追跡するための、広告の時間の最後のセグメント。

マニフェストサーバーは、 `VMAP1.0-conformant` XMLドキュメントを送信して、各広告の時間の開始と終了を追跡します。 これは、広告サーバーから返される実際のVMAP1.0応答のフィルタリングされたバージョンで、主に次に示すトラッキングイベントが含まれます。

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

マニフェストサーバーがプログラムコンテンツに挿入する広告クリエイティブごとに、VAST3.0準拠のXMLドキュメントを送信し、その広告を追跡します。 各XMLドキュメントには、挿入されるリニ `<InLine>``<Wrapper>` ア広告クリエイティブを説明する要素、またはラッパー広告（リンク広告やリダイレクト広告）の場合の要素、および関連するコンパニオン広告や拡張が含まれています。 VAST応答に、広告が広告ポッドの一部である場合など、シーケンス属性が含まれる場合、ドキュメントにはその属性が含まれます。 個々の広告を追跡するためのVAST3.0準拠のXMLドキュメントの例を以下に示します。

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

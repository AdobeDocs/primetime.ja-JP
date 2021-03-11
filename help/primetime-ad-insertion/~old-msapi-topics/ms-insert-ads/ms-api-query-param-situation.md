---
description: 基本的なクエリパラメーターに加えて、オプションのクエリパラメーターを使用すると、マニフェストサーバーが異なるクライアントや状況で機能するようになります。
title: クライアントおよび状況別のオプションのクエリパラメーター
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# クライアントと状況別のオプションのクエリパラメータ{#optional-query-parameters-by-client-and-situation}

基本的なクエリパラメーターに加えて、オプションのクエリパラメーターを使用すると、マニフェストサーバーが異なるクライアントや状況で機能するようになります。

## Akamai Ad Scaler {#section_120FEC75C34D4F4587B77D842166D68A}を使用した広告挿入

Akamaiコンテンツ配信ネットワーク(CDN)では、Akamai Edgeサーバーがクライアントとマニフェストサーバーの間の仲介として機能します。 Ad Scalerも使用する場合、`ptassetid`パラメーターと`live`クエリーパラメーターは、Akamai Edgeに必要な情報を提供します。

`ptassetid`パラメーターは、そのアセットの発行者のIDです。 Akamaiは、リクエストURLの一部として指定するbase64エンコードされたURLではなく、このURLを使用して、広告挿入用にマニフェストサーバーに提供するプレイリストを識別します。

`live`パラメーターは、ライブコンテンツとビデオオンデマンド(VOD)を区別します。 Akamaiとの合理化されたインターフェイスをサポートするために、マニフェストサーバーにこの情報が必要です。

Akamaiに関連するパラメーターを示すサンプルURLを次に示します。

```
https://. . .master.m3u8?. . .&ptassetid=pubAsset&live=true
```

## XboxのTVSDKからの広告挿入{#section_5DB405F4647240A0B83E72DE35D5EC80}

XboxのPrimetime TVSDKに基づくプレイヤーは、基本的なパラメーター以外のクエリパラメーターを追加で提供する必要はありません。

## Safariを使用したiOS上のTVSDKからの広告挿入{#section_250E493A125E4F82940D19C7DA2AAB2E}

Safariブラウザーを使用してiOS上のPrimetime TVSDKに基づくプレイヤーは、基本的なクエリパラメーターに加えて、`ptplayer`パラメーターと`live`パラメーターを指定する必要があります。

マニフェストサーバーは、`ptplayer`値`ios-mobileweb`を認識し、返される広告ステッチマニフェストからプリロールを削除します。

`live`パラメーターは、ライブコンテンツを返すか、VODコンテンツを返すかをマニフェストサーバーに指示します。

Safariを使用するiOSに関連するパラメーターを示すサンプルURLを次に示します。

```URL
https://. . .master.m3u8?. . .&ptplayer=ios-mobileweb&live=false
```

## カスタム広告キュー形式{#section_82AF880AAABE4BD4B593D906434D4D89}を使用した広告挿入

Adobeは、Primetimeパッケージで直接サポートされないAd Cue形式の名前を提供します。 このような形式を使用するには、`ptcueformat`パラメーターの値としてAdobe指定の名前を指定します。

カスタム広告キュー形式を指定するURLの例を以下に示します。

```URL
https://. . .master.m3u8?. . .&ptcueformat=[custom format name]
```

## 広告キューを使用したVOD用のFreeWheelタイムラインの作成{#section_E0D830F5EEE24639819B975B90F6999F}の広告挿入

広告キューを含むVODコンテンツを解析し、FreeWheel広告リクエストに含めるには、`ptcueformat`パラメーターの値を`DPIsimple`に設定します。

VODにFreeWheelタイムラインを使用する場合に指定するサンプルURLを以下に示します。

```URL
https://. . .master.m3u8?. . .&ptcueformat=DPISimple&live=false
```

## VOD {#section_F398F7659164463FA886A4CC787C7B5A}のカスタムタイムラインを使用した広告挿入

指定したタイムラインに従って、マニフェストサーバーに広告をVODコンテンツに挿入するように依頼するには、`pttimeline`パラメーターの値を、タイムラインを指定する文字列に設定します。 [VODタイムライン形式](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)を参照してください。

VOD用のカスタムタイムラインを使用するサンプルURLを以下に示します。

```URL
https://. . .master.m3u8?. . .&live=false&pttimeline=B,60,2,p;C,120,1;B,30,2,m;C,300,1
```

最大2つの広告を含む1分の最初の時間を指定し、その後に2分のコンテンツセグメントが続き、その後に最大2つの広告を含む30秒の時間が続き、その後に5分のコンテンツセグメントが続きます。

VODコンテンツのカスタムコンテンツタイムラインに対する広告の切り替えは、次のように動作します。

* 広告は、広告サーバーが指定した広告配置時間の後、最も近い時間の境界に表示されます。

* セグメントの長さは2秒以上です。

## TSセグメントの承認{#section_BF855A4399DC42CB8C0586113A416BBC}

Adobeでは、この機能はAkamai CDNに対してのみサポートされています。 HTTPライブストリーミング(HLS)は、ストリームレベルのM3U8プレイリストを使用して、トランスポートストリーム(TS)セグメントを配信します。 複数のストリームレベルの再生リストが、バリアントM3U8プレイリストでクライアントに提供されます。 クライアントは、バリアントリストから1つのプレイリストストリームを選択し、そのストリームレベルプレイリストのTSセグメントを1つずつダウンロードします。 通常の操作では、リクエストされたコンテンツにcookie認証が必要になる場合があります。cookie認証は、マニフェストサーバーがバックグラウンドで不可視に処理します。 これは、生コンテンツからcookieを抽出し、選択したプレイリストストリームのリクエストに使用するURLに適切なトークンを追加します。

BootstrapURLのクエリパラメーターに`pttoken=true`が含まれる場合、パブリッシャーは、ストリーム全体に対して1回だけではなく、各TSセグメントのリクエストにcookieを使用する必要があります。 マニフェストサーバーは、このcookieをクエリパラメーターとして、送信するストリームプレイリスト内の各TSセグメントURLに添付します。

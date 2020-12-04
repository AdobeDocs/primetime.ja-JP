---
title: TVSDK 2.1 PlayStation 4リリースノート
seo-title: TVSDK 2.1 PlayStation 4リリースノート
description: TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされる機能と既知の問題について説明します。
seo-description: TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされる機能と既知の問題について説明します。
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# TVSDK 2.1 PlayStation 4リリースノート{#tvsdk-playstation-release-notes}

TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされる機能と既知の問題について説明します。

## 解決された問題{#resolved-issues}

TVSDK 2.1 for PlayStation 4で解決された問題を次に示します。

**バージョン2.1.0.638**

* **PTPLAY-10439:VMAPラッパー広告リンクが壊れた**
とき、プレイヤーが準備中の状態で停止していた（送信されていなかった） 
`onComplete` を呼び出し元に送信する)。

* **PTPLAY-10179:**

   `creativeRepackaging` と `fallbackOnInvalidCreative` 値がデフォルトでオフになりました。また、`creativeRepackaging`フラグが設定されたが`creativeRepackaging`形式が指定されなかった場合、`onRepackagingComplete`は広告の時間に広告がある回数だけ呼び出され、広告の時間が複数回作成されていました。

* **Zendesk #10304**:広告の有効性のオン/オフ変数が初期化されませんでした。ここで、`DataSetEntry's`ベクトルから変数を初期化します。

* **PTPLAY-10318：バックグラウンドモードの**
サポートが導入されました。
* **Zendesk #17409：トリック再生モードに**
入り、通常再生モードに戻り、再びトリック再生モードに戻ると、再生位置がジャンプしていた問題を修正しました。
* **PTPLAY-9552：応答XMLファイルを解析**
した後、広告がない場合にエラーコード1108がpingされるようになりました。
* **PTPLAY-9551:Auditudeの処理**
後に広告の時間がない場合、CRSが呼び出されます。 
**onPrefetchCompleteはgroupCount** を減らします。広告の時間がないので、**groupCount**&#x200B;は0で、1ずつデクリメントされます。 以前は&#x200B;**groupCount**&#x200B;は&#x200B;**uint32_t**&#x200B;でしたが、このため最大値に変更されていました。 現在は&#x200B;**int32_t**&#x200B;です。

**バージョン2.1.0.621**

* **Zendesk #4555**
 Instant on Memory issues leading-Loading errors - 
`MediaItemLoader` リリース中に発生するクラッシュに関する修正  `mediaitemloader`

* **Zendesk #17223**
2.x CSAI:一部の広告トラッキングURLが発生しない
   * インライン広告を指すVAST広告に、追跡URLが含まれていない場合がありました。
   * VAST XMLの広告に複数のインプレッションタグがある場合、最初のインプレッションURLのみが保存され、残りは無視されました。 これで、すべてのインプレッションURLが保存され、後でピンジングされます。
* **Zendesk #17224**
PS4ユーザーエージェントがPrimetime情報をUAStringの最後に移動
* **Zendesk #17226**
2.x CSAI:一部の広告が繋がっているわけではありません。
\
   修正は、insertBy操作またはeraseBy操作によってタイムラインが変更されたことを示し、それに応じて期間を切り替えることです。

* **ゼンデスク#17284**
   [すべての] platformsクローズドキャプションは表示されません。\
   HLS - VTTキャプションファイル用の`EXT-X-MEDIA-TIME`タグをサポートします。

* **Zendesk #17889 PS4での「Milky」**
再生
\
   適用された正しいyoffset（カラー変換用）

* **Zendesk #17954**
広告のフォールバックロジック+空のvastの処理
\
   Vastラッパーの1つが空の場合、Vastパーサーを使用してラッパーの処理が続行される問題を修正しました。

* **Zendesk #17807**
 Zendesk #3103と同じ空き領域を越えることはできません。

* **Zendesk #17865 PS4およびXBox Oneの**
フォールバックロジック
\
   Zendesk #3103と同じ

**バージョン2.1.0.591**

* **Zendesk #3767**
PS4広告コードスニペット。VMAPリダイレクトを処理すると、広告解決に失敗します。
* **Zendesk #4096**
PS4 CSAI:セグメント化障害広告ライブラリがVMAP応答を処理する際に、TVSDKがセグメント化障害をスローした場合に発生するクラッシュを修正しました。

* **Zendesk #4161**
Trickplay 16xがムービーの最後でフリーズするトリック再生が通常の再生に戻ったときに行われるデッドロックが修正されました。

* **Zendesk #4208クローズドキャプションがオンの場合の**
ランダムクラッシュクローズドキャプションが有効な場合の固定メモリリーク

* **Zendesk #4213**
PS4 CSAI:すべての広告関連呼び出しに対するデフォルトのユーザーエージェント文字列の変更ブラウザーが使用しているのと同じUA文字列を使用してユーザーエージェント文字列が作成され、+ Primetime文字列を追加します。

* **PTPLAY-7675** （内部）トランスコードされた広告がVMAPまたはVAST応答内で呼び出されたときに、Creative Repackagingを再生できませんでした。修正は、広告が大量の場合にアセットから読み取るのではなく、広告からメディアファイルを読み取るだけです。

* **PTPLAY-7895** (internal): `allowMultipleAds=false` `allowMultipleAds` パラメーターが正しく従っていない場合に、広告が再生されないバグが修正されました。

* **PTPLAY-7896** (internal) PS4で広告が順番どおりに再生されない問題を修正しました。広告がXML応答に表示された順番とは異なる場合がありました。

* PS4 TVSDKは、ゲームではなくミニアプリで再テストしました。

**バージョン2.1.0.563**

* **Zendesk #3868**
 TVSDKは、Playstation SDK 2.5をサポートします。TVSDKは、2.5 Playstation SDKを使用して構築されました。

* **Zendesk #4093**
 targetingPt広告リクエストの情報キーと値のペア。
\
   キー/値のペアを区切る改行文字が追加されました。

## サポートされる機能{#supported-features}

TVSDK 2.1 for PlayStation 4では、以下の機能がサポートされています。

**バージョン2.1.0.621**

* 広告のフォールバック、広告選択ロジックのデイジーチェーン(Zendesk #3103)
フォールバックルールが有効になっているVAST広告（クリエイティブ）の場合、TVSDKは、無効なMIMEタイプを持つ広告を空として扱い、その場所でフォールバック広告を使用しようとします。フォールバック動作の一部を設定できます

**バージョン2.1.0.538**

* 再生、一時停止、シークを含むHLS VOD再生
* アダプティブビットレートストリーミング
* Primetime DRMおよびVanilla AESで保護されたコンテンツを使用した暗号化されたコンテンツ再生
* デフォルトの広告動作と広告の許可を持つクライアント側の広告挿入
* クリエイティブの再パッケージング
* WebVTTクローズドキャプション
* カスタム開始の位置で即時オン
* 早送りと巻き戻しによるトリック再生
* 302リダイレクト

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。
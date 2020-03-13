---
title: TVSDK 2.1 PlayStation 4リリースノート
seo-title: TVSDK 2.1 PlayStation 4リリースノート
description: TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされている機能と既知の問題について説明します。
seo-description: TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされている機能と既知の問題について説明します。
uuid: 494569cf-07e2-476a-b88e-e46c9cca4cdc
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: ebfc8819-f5a9-47a2-b454-0e4e6f9e4640
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# TVSDK 2.1 PlayStation 4リリースノート {#tvsdk-playstation-release-notes}

TVSDK 2.1 for PlayStation 4リリースノートでは、TVSDK 2.1 PlayStation 4でサポートされている機能と既知の問題について説明します。

## 解決された問題 {#resolved-issues}

PlayStation 4向けのTVSDK 2.1に関する解決済みの問題を次に示します。

**バージョン2.1.0.638**

* **PTPLAY-10439:** VMAPラッパー広告リンクが切断されたとき、プレイヤーが準備中の状態で停止していた(呼び出し元に送信されて `onComplete` いなかった)問題を修正しました。

* **PTPLAY-10179:**
   `creativeRepackaging` と値がデ `fallbackOnInvalidCreative` フォルトでオフになりました。 また、フラグが設 `creativeRepackaging` 定されたが、形式が指定さ `creativeRepackaging``onRepackagingComplete` れなかった場合、広告の時間に広告があった回数だけ広告が呼び出され、広告の時間が複数回作成されていました。

* **Zendesk #10304**:広告の有効性のオン/オフ変数が初期化されませんでした。 ここで、変数をctorから初期化 `DataSetEntry's` します。

* **PTPLAY-10318:**&#x200B;バックグラウンドモードのサポートが導入されました。
* **ゼンデスク# 17409:**&#x200B;トリック再生モードに入り、通常再生モードに戻り、再びトリック再生モードに戻ると、再生位置がジャンプしていた問題を修正しました。
* **PTPLAY-9552:**&#x200B;応答XMLファイルを解析した後、広告が存在しない場合は常にエラーコード1108がpingされるようになりました。
* **PTPLAY-9551:** Auditudeの処理後に広告の時間がない場合、CRSはonPrefetchCompleteを呼び出し **て** 、groupCountを減少します。 広告の時間がないので、 **groupCountは** 0で、1ずつ減らされます。 以前は、 **groupCount** は **uint32_tでした** 。これは、以前はこの値がmax値に変更されていたためです。 現在は **int32_tです**。

**バージョン2.1.0.621**

* **Zendesk #4555 Instant on** Memory issues leading-Loading errors — リリース中にクラッシュが発 `MediaItemLoader` 生する問題を修正しました。 `mediaitemloader`

* **Zendesk #17223** 2.x CSAI:一部の広告追跡URLが発生しない
   * インライン広告を指す一部のVAST広告に、追跡URLが見つかりませんでした。
   * VAST XMLの広告に複数のインプレッションタグが含まれている場合、最初のインプレッションURLのみが保存され、残りは無視されました。 これで、すべてのインプレッションURLが保存され、後でPINGされます。
* **Zendesk #17224** PS4ユーザーエージェントがプライマタイム情報をUAStringの最後に移動
* **Zendesk #17226** 2.x CSAI:すべての広告が繋がっているわけではありません。\
   この問題は、insertByまたはeraseBy操作によってタイムラインが変更されたことを示し、それに応じて期間を切り替えることで修正されました。

* **ゼンデスク#17284**
   [すべてのプラットフォーム] （クローズドキャプション）が表示されません。\
   HLS - VTTキャプションファイルの `EXT-X-MEDIA-TIME` タグのサポート。

* **Zendesk #17889 PS4**&#x200B;での「天の」再生\
   適用された正しいヨフセット（カラー変換用）

* **Zendesk #17954広告のフォールバ**&#x200B;ックロジック+空の大容量の処理\
   Vastラッパーの1つが空の場合、Vastパーサーがラッパーの処理を続けるのに使用されていた問題を修正しました。

* **Zendesk #17807空の** vastを超えることはできません。Zendesk #3103と同じです。

* **Zendesk #17865 PS4お**&#x200B;よびXBox Oneのフォールバックロジック\
   Zendesk #3103と同じ

**バージョン2.1.0.591**

* **Zendesk #3767** PS4広告コードスニペット。VMAPリダイレクトの処理時に広告解決が失敗します。
* **Zendesk #4096** PS4 CSAI:セグメントの障害TVSDKが広告ライブラリがVMAP応答を処理する際にセグメント化障害をスローする場合に、セグメント化の障害が修正されました。

* **Zendesk #4161ムービーの最**&#x200B;後に16xがトリックされ、フリーズが発生するトリック再生が通常の再生に戻ったときのデッドロックの修正

* **Zendesk #4208クローズドキャプ**&#x200B;ションがオンの場合のランダムクラッシュクローズドキャプションが有効な場合のメモリリークを修正。

* **Zendesk #4213** PS4 CSAI:すべての広告関連呼び出しのデフォルトのユーザーエージェント文字列を変更するユーザーエージェント文字列は、ブラウザーで使用しているのと同じUA文字列+ Primetime文字列を追加して作成されます。

* **PTPLAY-7675** （内部）トランスコードされた広告が再生されない。VMAPまたはVAST応答内で呼び出されたときに、クリエイティブの再パッケージ化が失敗していた問題を修正しました。 大量の広告の場合、アセットから読み取るのではなく、広告からメディアファイルを読み取るだけに修正しました。

* **PTPLAY-7895** （内部）：パラメー `allowMultipleAds=false`ターが正しく使用されない場合に、広告playFixedバ `allowMultipleAds` グが表示されない問題を修正しました。

* **PTPLAY-7896** （内部）PS4で広告が順番に再生されない問題を修正しました。XML応答で広告が表示された順序に広告が含まれない問題を修正しました。

* PS4 TVSDKは、ゲームの代わりにミニアプリ内で再テストしました。

**バージョン2.1.0.563**

* **Zendesk #3868** TVSDKは、Playstation SDK 2.5をサポートします。TVSDKは、2.5 Playstation SDKを使用して構築されました。

* **Pt広告リクエストのZendesk #4093** targetingInfoキーと値のペア。\
   キーと値のペアを区切る改行文字が追加されました。

## サポートされる機能 {#supported-features}

TVSDK 2.1 for PlayStation 4では、次の機能がサポートされています。

**バージョン2.1.0.621**

* 広告のフォールバック、広告選択ロジックのデイジーチェーン(Zendesk #3103)フォールバックルールが有効なVAST広告（クリエイティブ）の場合、TVSDKは無効なMIMEタイプの広告を空の広告として扱い、代替広告を使用します。フォールバック動作の一部を設定できます

**バージョン2.1.0.538**

* HLS VOD再生（再生、一時停止、シークを含む）
* アダプティブビットレートストリーミング
* Primetime DRMおよびバニラAESで保護されたコンテンツを使用した暗号化されたコンテンツ再生
* デフォルトの広告動作と広告の許容性を持つクライアント側の広告挿入
* クリエイティブの再パッケージ化
* WebVTTクローズドキャプション
* カスタムの開始位置で即時オン
* 早送りと巻き戻しによるトリック再生
* 302リダイレクト

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。
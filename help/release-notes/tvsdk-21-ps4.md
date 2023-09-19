---
title: TVSDK 2.1 PlayStation 4 リリースノート
description: PlayStation 4 向け TVSDK 2.1 リリースノートでは、 TVSDK 2.1 PlayStation 4 でサポートされる機能と既知の問題について説明します。
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# TVSDK 2.1 PlayStation 4 リリースノート {#tvsdk-playstation-release-notes}

PlayStation 4 向け TVSDK 2.1 リリースノートでは、 TVSDK 2.1 PlayStation 4 でサポートされる機能と既知の問題について説明します。

## 解決された問題 {#resolved-issues}

以下は、PlayStation 4 向けの TVSDK 2.1 で解決された問題です。

**バージョン 2.1.0.638**

* **PTPLAY-10439:**
VMAP ラッパー広告リンクが壊れた場合、プレーヤーは準備状態で停止していました（送信されていませんでした）。 `onComplete` を呼び出し元に送信する )。

* **PTPLAY-10179:**
  `creativeRepackaging` および `fallbackOnInvalidCreative` の値は、デフォルトでオフになりました。 また、 `creativeRepackaging` フラグは設定されましたが、何もありません `creativeRepackaging` 形式が指定された場合、 `onRepackagingComplete` が広告ブレーク内の広告と同じ回数呼び出され、広告ブレークが複数回作成されました。

* **Zendesk #10304**：広告活性のオン/オフ変数が初期化されませんでした。 ここでは、から変数を初期化します。 `DataSetEntry's` ctor.

* **PTPLAY-10318:**
バックグラウンドモードのサポートが導入されました。
* **Zendesk # 17409:**
トリック再生モードに入り、通常再生モードに戻り、再びトリック再生モードに入ると、再生位置がジャンプしていました。
* **PTPLAY-9552:**
応答 XML ファイルを解析した後、広告が存在しない場合は常にエラーコード 1108 が ping されるようになりました。
* **PTPLAY-9551:**
Auditude処理の後に広告ブレークがない場合、 CRS はを呼び出します。 **onPrefetchComplete** groupCount を減らします。 広告ブレークがないので、 **groupCount** は 0 で、1 ずつ減らされます。 以前は **groupCount** が **uint32_t** その理由は、以前は最大値に変更されていたからです。 これは、 **int32_t**.

**バージョン 2.1.0.621**

* **Zendesk #4555**
メモリ上の即時実行時の問題のリーディング — ロードエラー — `MediaItemLoader` リリース時にクラッシュが発生する問題を修正 `mediaitemloader`

* **Zendesk #17223**
2.x CSAI：一部の広告トラッキング URL が実行されない
   * 次にインライン広告を指す一部の VAST 広告に、トラッキング URL が欠落していました。
   * VAST XML の広告に複数のインプレッションタグがある場合、最初のインプレッション URL のみが保存され、残りは無視されました。 これで、すべてのインプレッション URL が保存され、後で ping が送信されます。
* **Zendesk #17224**
PS4 ユーザーエージェントが UAString の最後に primetime 情報を移動
* **Zendesk #17226**
2.x CSAI：すべての広告が関連付けられているわけではありません。\
  修正は、insertBy 操作または eraseBy 操作によってタイムラインが変更されたことを示し、それに応じて期間切り替えを行うことです。

* **Zendesk #17284**
  [すべてのプラットフォーム] クローズドキャプションは表示されません。\
  HLS — のサポート `EXT-X-MEDIA-TIME` タグを使用して、VTT キャプションファイルにアクセスできます。

* **Zendesk #17889**
PS4 で再生「乳の」\
  適用された正しいオフセット（カラー変換用）

* **Zendesk #17954**
広告のフォールバックロジック+空の vast の処理\
  Vast ラッパーの 1 つが空の場合、Vast パーサーがラッパーの処理を続行するために使用されていた問題を修正しました。

* **Zendesk #17807**
Zendesk #3103と同じ空の広大を過去に取得できません

* **Zendesk #17865**
PS4 および XBox One のフォールバックロジック\
  Zendesk #3103と同じ

**バージョン 2.1.0.591**

* **Zendesk #3767**
PS4 広告コードスニペットで、VMAP リダイレクトを処理する際に広告解決が失敗します。
* **Zendesk #4096**
PS4 CSAI：セグメント化障害 TVSDK が VMAP 応答を処理しているときにセグメント化障害をスローした場合に、セグメント化障害が修正されました。

* **Zendesk #4161**
映画の最後に 16 倍のトリックプレイがフリーズトリックプレイが通常の再生に戻ったときに発生するデッドロックの修正

* **Zendesk #4208**
クローズドキャプションがオンの場合のランダムクラッシュクローズドキャプションが有効な場合の固定メモリリーク

* **Zendesk #4213**
PS4 CSAI：すべての広告関連呼び出しのデフォルトのユーザーエージェント文字列を変更するユーザーエージェント文字列は、ブラウザーが+ Primetime 文字列を追加するのと同じ UA 文字列を使用して作成されます

* **PTPLAY-7675** （内部）トランスコードされた広告が、VMAP または VAST 応答内で呼び出された場合、クリエイティブの再パッケージングに失敗していた問題を再生しませんでした。 修正では、広告が大量にある場合、アセットから読み取るのではなく、広告から mediafile を読み取るだけです。

* **PTPLAY-7895** （内部） `allowMultipleAds=false`、広告が再生されない場合、 `allowMultipleAds` パラメーターが正しく追跡されていませんでした。

* **PTPLAY-7896** （内部）PS4 で広告が順不同で再生されています XML 応答で広告が表示された順序に広告がない問題を修正しました。

* PS4 TVSDK は、ゲームの代わりにミニアプリ内で再テストしました。

**バージョン 2.1.0.563**

* **Zendesk #3868**
TVSDK は Playstation SDK 2.5 をサポートしていますか。 TVSDK は、2.5 Playstation SDK を使用して構築されました。

* **Zendesk #4093**
Pt Ads リクエストの targetingInfo キーと値のペア。\
  キーと値のペアを区切る改行文字が追加されました。

## サポートされる機能 {#supported-features}

TVSDK 2.1 for PlayStation 4 では、次の機能がサポートされています。

**バージョン 2.1.0.621**

* Ad Fallback, Daisy chaining in ad selection logic (Zendesk #3103) フォールバックルールが有効な VAST 広告（クリエイティブ）の場合、 TVSDK は無効な MIME タイプの広告を空の広告として扱い、代わりにフォールバック広告を使用しようとします。フォールバック動作の側面を設定できます

**バージョン 2.1.0.538**

* HLS VOD 再生（再生、一時停止、シークを含む）
* アダプティブビットレートストリーミング
* Primetime DRM と Vanilla AES で保護されたコンテンツを使用した暗号化されたコンテンツ再生
* デフォルトの広告動作と許容度を備えたクライアントサイド広告の挿入
* クリエイティブの再パッケージ化
* WebVTT クローズドキャプション
* カスタムの開始位置ですぐにオン
* 早送りと巻き戻しでのトリック再生
* 302 リダイレクト

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://experienceleague.adobe.com/docs/primetime.html) ページに貼り付けます。

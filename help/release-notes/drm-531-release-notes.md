---
title: DRM 5.3.1 のリリースノート
description: DRM 5.3.1 リリースノートでは、DRM 5.3.1 の新機能と既知の問題について説明します。
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# DRM 5.3.1 のリリースノート {#drm-release-notes}

DRM 5.3.1 リリースノートでは、DRM 5.3.1 の新機能と既知の問題について説明します。

## バージョン 5.3 の新機能 {#new-features}

* **セキュア停止 —** 再生を停止するか、再生ウィンドウの最後に続くかを指定できます。
* **解像度ベースの出力保護 (RBOP) -** 出力の制約は、ピクセル解像度に基づいて指定できます。
* **CDM ゲート —** HTML5 をサポートするために、Adobeは、Adobe Primetime DRM( 以前のAdobeアクセス DRM)Java SDK に含まれる参照実装ライセンスサーバーを更新し、1 つの URL エンドポイントですべての DRM プロトコルメッセージを使用できるようにしました。 CDM(Content Decrypting Module)DRM ベンダーが実装する必要があるHTML5 EME(Encrypted Media Extension) 仕様に準拠するために、HTTP URL メソッドのこの統合が必要です。 以前は、参照実装ライセンスサーバーによって公開されている URL エンドポイントは次のみでした。

   * /flashaccess/i15n/v3 （個別化）
   * /flashaccess/license/v5 （ライセンスリクエスト）
   * /flashaccess/licenseRet/v5 （ライセンスリターン）
   * /flashaccess/getServerVersion/v5 （サーバーのバージョンの取得）

現在は、(HTML5 CDM からの ) すべてのリクエストを単一のエンドポイント (/req) に転送できます。

この変更は、Flash Player、Android、iOSなど、CDM 以外のプラットフォームとの後方互換性があります。

* **RBOP ダウンスケーリング —** RBOP にはHTML5 スペースに固有の自動ダウンスケーリング機能が含まれます。DRM ポリシーで指定された許容ビットレートを超えるビットレートの場合、コンテンツは最大許容解像度にダウンスケーリングされます。 例えば、1080p ストリームが、HDCP に準拠していないモニターにコンテンツを表示しているクライアントにストリーミングされる場合、DRM ポリシーによって、最大解像度が 720p である必要があると示される場合があります。 Primetime DRM は、1080p ストリームをデコードし、画面にレンダリングする前に 720p にダウンスケールします。 ビデオを再生しているブラウザーを HDCP をサポートしているモニターにドラッグすると、Primetime DRM はコンテンツの縮小を停止し、1080 で再生できるようになります。

## バージョン 5.3 の既知の問題 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` ログメッセージを出力 `flashaccess-global.log.`必ず `flashaccess-global.log` ファイルは、Hasher.bat と同じディレクトリにあります。

* 一部の `toJSON()`コールリターン `Strings` JSON に完全に準拠していないか、完全に準拠していない（つまり、JSON 構造の構成がない）スタンドアロンの方法である。

* Xbox キーサーバーは、バージョン値が 1 に等しくないキーリクエストを受け付けています。

Xbox キーサーバーは、バージョンが 1 のキーリクエストのみをサポートする必要がありますが、現在は、バージョンが 1 でないキーリクエストをサーバーが受け付けています。

* Xbox キーサーバーは、ポリシーを正しく検証しません。

Xbox キーサーバーは有効期限の日付以外のポリシーを受け付けるべきではありませんが、現在は、サーバーはそれらを受け付けています。

* Xbox キーサーバは、間違ったパッケージャーの証明書で作成されたメタデータを含むキー要求を拒否する必要があります。
* 一部の JSON 構造の戻り値が、解決に基づく出力保護関連のクラスに対して正しく形式設定されていません。

いくつかのクラスは、toJSON() メソッドを実装します。このメソッドは、そのオブジェクトの JSON 準拠表現を文字列として返す必要がありますが、現在返される値は完全には JSON に準拠していません。

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。

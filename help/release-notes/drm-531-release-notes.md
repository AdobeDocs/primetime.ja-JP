---
title: DRM 5.3.1リリースノート
seo-title: DRM 5.3.1リリースノート
description: DRM 5.3.1リリースノートでは、DRM 5.3.1の新機能と既知の問題について説明します。
seo-description: DRM 5.3.1リリースノートでは、DRM 5.3.1の新機能と既知の問題について説明します。
uuid: bb61b79f-a5b3-42ed-8016-495b1ac99ea6
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# DRM 5.3.1リリースノート {#drm-release-notes}

DRM 5.3.1リリースノートでは、DRM 5.3.1の新機能と既知の問題について説明します。

## バージョン5.3の新機能 {#new-features}

* **セキュア停止** — 再生ウィンドウの最後で再生を停止するか、続行するかを指定できます。
* **Resolution Based Output Protection(RBOP)** — ピクセル解像度に基づいて出力制約を指定できます。
* **CDMのゲーティング —** HTML5をサポートするために、アドビは、Adobe Primetime DRM（旧称Adobe Access DRM）Java SDKに含まれるリファレンス実装ライセンスサーバーを、1つのURLエンドポイントですべてのDRMプロトコルメッセージを使用できるように更新しました。 CDM(Content Decryption Module)のDRMベンダーが実装する必要があるHTML5 EME(Encrypted Media Extension)仕様に準拠するために、このHTTP URLメソッドの統合が必要です。 以前は、参照実装ライセンスサーバーによって公開されたURLエンドポイントは、次の2つのみでした。

   * /flashaccess/i15n/v3（個別化）
   * /flashaccess/license/v5（ライセンス要求）
   * /flashaccess/licenseRet/v5 （ライセンスの返却）
   * /flashaccess/getServerVersion/v5（サーバーのバージョンの取得）

現在は、（HTML5 CDMからの）すべてのリクエストを単一のエンドポイントに送信できます。/req

この変更は、Flash Player、Android、iOSなど、CDM以外のプラットフォームとの下位互換性があります。

* **RBOPダウンスケーリング —** HTML5領域に固有のRBOPには自動ダウンスケーリング機能が含まれています。DRMポリシーで指定された許容ビットレートを超えるビットレートの場合、コンテンツは最大許容解像度にダウンスケールされます。 例えば、1080pストリームが、HDCP非対応のモニターでコンテンツを表示しているクライアントにストリーミングされる場合、DRMポリシーによっては最大解像度が720pであることが示される場合があります。 Primetime DRMは1080pストリームをデコードし、720pに縮小してから画面にレンダリングします。 その後、ビデオを再生しているブラウザーをHDCPをサポートしているモニターにドラッグすると、Primetime DRMはコンテンツのダウンスケールを停止し、1080で再生できるようになります。

## バージョン5.3の既知の問題 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` ログメッセージをHasher.bat `flashaccess-global.log.`と同じディレクトリ `flashaccess-global.log` にあることを確認する必要があります。

* 一部の呼び出しの出力は、完全 `toJSON()`なJSON `Strings` 準拠ではないか、スタンドアロンの方法（JSON構造の組み合わせなし）で完全に準拠していないものを返します。

* Xboxキーサーバーは、バージョンの値が1以外のキー要求を受け付けます。

Xboxキーサーバーは、バージョンが1のキー要求のみをサポートしますが、現在は、バージョンが1でないキー要求を受け付けています。

* Xboxキーサーバーはポリシーを正しく検証しません。

Xboxキーサーバーは、有効期限を超えたポリシーを受け入れないでください。現在は、そのポリシーは受け入れられます。

* Xboxキーサーバーは、間違ったパッケージャー証明書で作成されたメタデータを含むキー要求を拒否する必要があります。
* 一部のJSON構造の戻り値が、解像度ベースの出力保護関連のクラスに対して正しく形式設定されていません。

いくつかのクラスは、toJSON()メソッドを実装します。このメソッドは、そのオブジェクトのJSON準拠の表現を文字列として返す必要がありますが、現在のところ、返される値は完全にJSONに準拠していません。

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeのラーニングとサポートページで参照してください](https://helpx.adobe.com/support/primetime.html) 。

---
title: DRM 5.3.1リリースノート
description: DRM 5.3.1リリースノートでは、DRM 5.3.1の新機能と既知の問題について説明します。
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---


# DRM 5.3.1リリースノート{#drm-release-notes}

DRM 5.3.1リリースノートでは、DRM 5.3.1の新機能と既知の問題について説明します。

## バージョン5.3の新機能{#new-features}

* **安全な停止 —** 再生ウィンドウの最後で再生を停止するか、続行するかを指定できます。
* **Resolution Based Output Protection(RBOP)：ピクセル解像度** に基づいて出力制約を指定できます。
* **CDMゲーティング — HTML5** をサポートするために、Adobeは、Adobe PrimetimeDRM(旧称AdobeアクセスDRM)Java SDKに含まれるリファレンス実装ライセンスサーバーを更新し、1つのURLエンドポイントですべてのDRMプロトコルメッセージを使用できるようにしました。CDM(Content Decryption Module)DRMベンダーが実装する必要があるHTML5 EME(Encrypted Media Extension)仕様に準拠するために、HTTP URLメソッドの統合が必要です。 以前は、参照実装のライセンスサーバーで公開されているURLエンドポイントは次のみです。

   * /flashaccess/i15n/v3（個別化）
   * /flashaccess/license/v5（ライセンスリクエスト）
   * /flashaccess/licenseRet/v5（ライセンスリターン）
   * /flashaccess/getServerVersion/v5（サーバーのバージョンの取得）

現在は、（HTML5 CDMからの）すべてのリクエストを単一のエンドポイントに送信できます。/req

この変更は、Flash Player、Android、iOSなど、CDM以外のプラットフォームとの下位互換性があります。

* **RBOPダウンスケーリング — HTML5スペース** に固有のRBOPには自動ダウンスケーリング機能が含まれます。DRMポリシーで指定された許容ビットレートを超えるビットレートの場合、コンテンツは最大許容解像度にダウンスケールされます。例えば、1080pストリームが、HDCP非対応のモニターにコンテンツを表示しているクライアントにストリーミングされる場合、DRMポリシーは、最大解像度が720pである必要があることを示している可能性があります。 Primetime DRMは1080pストリームをデコードし、720pに縮小してから画面にレンダリングします。 ビデオを再生しているブラウザーをHDCPをサポートしているモニターにドラッグすると、Primetime DRMは、コンテンツのダウンスケールを停止し、1080で再生できるようになります。

## バージョン5.3の既知の問題{#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` ログメッセージを出力 `flashaccess-global.log.`します。 `flashaccess-global.log` ファイルがHasher.batと同じディレクトリにあることを確認する必要があります。

* 一部の`toJSON()`呼び出しの出力は、完全なJSONに準拠していない、または完全に準拠していない`Strings`を返します（JSON構造体の組み合わせがないなど）。

* Xboxキーサーバーは、バージョンの値が1以外のキー要求を受け付けます。

Xboxキーサーバーは、バージョンが1のキー要求のみをサポートする必要がありますが、現在は、バージョンが1でないキー要求を受け付けています。

* Xboxキーサーバーは、ポリシーを正しく検証できません。

Xboxキーサーバーは、有効期限を超えたポリシーを受け付けることはできませんが、現在は、サーバーが受け付けます。

* Xboxキーサーバーは、不正なパッケージャー証明書で作成されたメタデータを含むキー要求を拒否する必要があります。
* 一部のJSON構造の戻り値が、解像度ベースの出力保護関連のクラスに対して正しく形式設定されていません。

いくつかのクラスで、toJSON()メソッドを実装します。このメソッドは、そのオブジェクトのJSON準拠表現をStringとして返す必要がありますが、現在、返される値は完全なJSONに準拠していません。

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。

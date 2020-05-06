---
title: PTAI 20.3.3リリースノート
description: PTAI 20.5.1のリリースノートでは、2020年のPrimetime Dynamic Ad Insertionで解決され、既知の問題である、新機能や変更点について説明します。
translation-type: tm+mt
source-git-commit: 2a5866be64895ba13994720bf943dc676c2595bf
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Primetime Dynamic Ad Insertion 20.5.1リリースノート

Dynamic Ad Insertion 20.5.1のリリースノートでは、2020年のPrimetime Dynamic Ad Insertionの新機能や変更点、解決された問題、既知の問題について説明します。

## PTAI 20.5.1の新機能

**日時：** 2020年5月5日火曜日午前04:00 ～東部午前5:00

* If-Modified-Sinceヘッダーが送信される場合に、正しいCORSヘッダーが提供される問題を修正しました。

* CRSダッシュボードのバグが修正されました。

* メンテナンスの更新。

## 以前のリリースでの変更点

### バージョン20.3.4

**日時：** 2020年4月1日水曜日午前03:00 ～東部の午前4:00

* VOD/WebVTTに広告を挿入した後、サブタイトルが同期されない問題を修正しました。

* セキュリティ更新。

### バージョン20.3.3

**日時：** 2020年3月26日木曜日午前03:00～東部午前4:00

* SSAI 4XXおよび5XX応答は、CORS関連のヘッダーを正しく供給するようになり、クロスドメインjavascript/webviewクライアントがエラー応答を正常に読み取れるようになりました。

* X-Forwarded-Forヘッダーの問題を修正しました。広告サーバーに渡されると、IPv6アドレスが正しくURLエンコードされませんでした。

* CMAF/デミュックスされたオーディオストリームで、特定のシナリオでEXT-X-MEDIA-SEQUENCE番号が正しく増加しない問題を修正しました。

### バージョン20.1.3

**日時：** 2020年1月28日火曜日午前2時から東部午前3時まで

* **&quot;nbc&quot; CueFormat** Convert cues from FER streamをFWタイムラインオーバーライドパラメーターに変換できるVMAP。ptcueformat=nbcが使用され、ストリームがマニフェスト内キューとベイクイン広告を含むVODストリームの場合。

* サードパーティの広告プロバイダー/CDNに転送する前に、HTTPヘッダーのuser-agentフィールドの内容を変更します。

* Auditudeや他の広告プロバイダーCDNに送信する前に、「user-agent」HTTPヘッダーから制御/印刷不可文字（asciiコード&lt; 32）をフィルターで除外します。 Auditude Ad-Callが、このような無効なヘッダーで失敗するために使用されます。

* 古いV1オブジェクトをNetStorageグループから削除して、Akamaiの安全な範囲内にオブジェクト数を維持します。

## 解決された問題

レポートされた問題に解決が関連付けられている場合は、Zendesk参照が表示されます。 例えば、ZD#xxxxx。

**PTAI 20.3.3**

* X-Forwarded-Forヘッダーに関する問題。広告サーバーに渡す際にIPv6アドレスが正しくURLエンコードされていなかった問題を修正しました。

* CMAF/デミュックスされたオーディオストリームに関する問題。特定のシナリオで、EXT-X-MEDIA-SEQUENCE番号が特定のシナリオで誤って増加する場合があります

## 既知の問題と制限事項

**PTAI 20.3.3**

新しい制限は追加されませんでした。

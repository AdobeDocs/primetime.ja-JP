---
description: AppleのHLSスタックは、プライマリセットのストリームを取得できない場合に、フェイルオーバー/バックアップストリームへの切り替えをサポートします。 Apple HLSデバイスでは、フェイルオーバーを容易にするために、マニフェストサーバーにシグナルを送信して、マスタープレイリストで識別されるプライマリストリームとフェイルオーバーストリームを、独自のUUIDで結合されたセットとして扱うことができます。
seo-description: AppleのHLSスタックは、プライマリセットのストリームを取得できない場合に、フェイルオーバー/バックアップストリームへの切り替えをサポートします。 Apple HLSデバイスでは、フェイルオーバーを容易にするために、マニフェストサーバーにシグナルを送信して、マスタープレイリストで識別されるプライマリストリームとフェイルオーバーストリームを、独自のUUIDで結合されたセットとして扱うことができます。
seo-title: フェイルオーバー/バックアップ・ストリームへのHLSプレーヤーの切り替えの促進
title: フェイルオーバー/バックアップ・ストリームへのHLSプレーヤーの切り替えの促進
uuid: 2fea8a51-e4cb-4fc9-82d5-6305a1d96603
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# フェイルオーバー/バックアップ・ストリームへのHLSプレーヤーの切り替えの容易化{#facilitating-hls-player-switching-to-failover-backup-streams}

AppleのHLSスタックは、プライマリセットのストリームを取得できない場合に、フェイルオーバー/バックアップストリームへの切り替えをサポートします。 Apple HLSデバイスでは、フェイルオーバーを容易にするために、マニフェストサーバーにシグナルを送信して、マスタープレイリストで識別されるプライマリストリームとフェイルオーバーストリームを、独自のUUIDで結合されたセットとして扱うことができます。

Apple HLSデバイス上のフェイルオーバーストリームまたはバックアップストリームへの切り替えを容易にするために、BootstrapURLに`ptfailover`パラメーターを指定できます。 このパラメーターを指定する場合、マニフェストサーバーは、各フェイルオーバーセットに対して個別の再生セッション（広告のステッチを決定する）を作成します。

## 詳細

Bootstrap要求に`ptfailover=true`を含めた場合、SSAIがフェイルオーバー/バックアップへのHLS切り替えをどのように処理するか

* マスタープレイリストにプライマリおよびバックアップセットが含まれる場合：

   * マニフェストサーバは、AVストリームURLの`BANDWIDTH`属性と解析順を使用して、異なるフェイルオーバーセット用のAVストリームURLを識別する。 別々の内部再生セッション（個別のUUIDで識別）を作成し、異なる再生セッションを識別する異なるUUIDを持つマニフェストサーバーを指すストリームURLを作成します。
   * マニフェストサーバーは、一致する`RESOLUTION`属性とI-FrameストリームURLの解析順序を使用して、異なるフェールオーバーセット用のI-FrameストリームURLを識別します。 SSAIは、SSAIを指すI-FrameストリームURLに対して、関連するAVストリームを識別するUUIDを使用します。
   * この機能の場合、マニフェストサーバーは、マスタープレイリストのURI属性を持たない`EXT-X-MEDIA`グループのみをサポートします。
   * マニフェストサーバーは、`X-Object-Too-Old: true`ヘッダーを持つCDNから404エラー応答を検出し、ステータスコードとヘッダーをプレイヤーに送信する際に保持します。

* プリロール広告はプライマリセットにのみ追加されます。プレイヤーがフェイルオーバーストリームに切り替えたときに、誤ったプリロール広告や重複したプリロール広告が発生しないように、フェイルオーバーセットでは完全に無効になります。

---
title: マニフェストサーバークエリパラメーター
description: クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、そのクライアントがマニフェストサーバーに何を求めているかを伝えます。 必須の形式や値が必要な場合もあります。
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---


# マニフェストサーバークエリパラメーター{#ms-query-params}

クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、そのクライアントがマニフェストサーバーに何を求めているかを伝えます。 必須の形式や値が必要な場合もあります。

完全なURLは、ベースURLの後に疑問符が続き、`parameterName=value`引数が続いて、アンパサンドで区切られて構成されます。`Base URL?name1=value1&name2=value2& . . .&name n=value n`.

## 認識されるパラメータ{#section_072845B7FA94468C8068E9092983C9E6}

マニフェストサーバーは、以下のパラメーターを認識します。 広告サーバーに対して、認識されていないすべてのパラメーターと共に、これらのパラメーターを処理または渡します。

| キー | 説明 | 必須 | 有効な値 |
|---|---|---|---|
| `__sid__` | マニフェストサーバーがセッションIDの生成に使用する一意のID。 | はい | 英数字 |
| g | クライアントデバイスタイプ | ターゲットルールがデバイスタイプに依存する場合 | [Client Types](https://adobeprimetime.zendesk.com)のリストを参照してください。 Zendeskへのアクセスが必要です。 |
| k | カスタム広告ターゲット設定のキーワード | いいえ | `key1=value1;key2=value2;. . .`形式のURLセーフ文字列 |
| u | Primetime広告挿入アセットID。 | はい | MD5ハッシュ値 |
| z | アセットのPrimetime広告挿入ゾーンID。 | はい | 整数 |
| enableC3 | クライアントがC3ウィンドウ内にある。 trueの場合は、ローカルの使用可能なもののみを置き換えます。それ以外の場合は、使用可能なすべてを置き換えます。 | いいえ | ブール値 |
| live | コンテンツがライブストリームかVOD（ビデオオンデマンド）ストリームかを示します。 | Akamai Ad ScalerまたはiOS Safariクライアント。 | ブール値 |
| `pabimode` | [部分的な広告ブレークの](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) 挿入サポートを有効にします。<br> trueまたは開始の場合に有効にします。<br> falseの場合は無効にします。 | いいえ（デフォルトは無効） | 開始、trueまたはfalse |
| `ptadwindow` | 広告切り替えウィンドウの時間（秒）:DVRユーザーがストリームに参加した場合に広告を探す距離。 | いいえ（デフォルト= 1800） | 0 ～ 1800 |
| `ptassetid` | 投稿者によって割り当てられ、管理されるコンテンツの一意のIDです。 | Akamai Ad Scaler | URLセーフ文字列 |
| `ptcdn` | トランスコードされたアセットをホストするための1つ以上のCDNのリスト。 [マルチCDNのサポート](/help/primetime-ad-insertion/~old-creative-repackaging-service/multi-cdn-supportt.md)を参照してください。 | いいえ（デフォルト=Akamai） | 例：Akamai、Level3、Limelight、Comcast |
| `ptcueformat` | M3U8に存在するカスタム広告キュー形式の名前。 | いいえ | DPISimple、DPIScte35、Elemental、NBC、NFL、またはTurner |
| `ptfailover` | マスタープレイリストで指定されているプライマリストリームとフェイルオーバーストリームを識別し、それらを別々のセットとして扱うようマニフェストサーバーに通知します。 これにより、フェイルオーバーが容易になり、タイミングエラーが発生するのを防ぎます。 （Apple HLSデバイスのみ）。 [HLSプレーヤーの切り替えの容易化](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/hls-switching-to-failover.md)を参照してください。 | いいえ | true |
| `ptmulticall` | trueに設定した場合、FERに対する複数のAuditude広告呼び出しが行われ、広告の時間ごとに1つ 存在しない場合、またはfalseに設定された場合、FERのauditudeに対して1つの広告呼び出しが行われます。 | いいえ | ブール値<br> **注意**:次の要件が必要です。 <ul><li>`ptcueformat` パラメーターはnbcに設定する必要があります</li><li>pttimelineパラメーターは無視されます。</li></ul> |
| `ptplayer` | プレイヤーがリクエストを行いました。 | iOS/Safari | ios-mobileweb |
| `ptrendition` | 広告挿入によって自動生成され、Akamaiで使用されます。 追加または削除しない。 | Akamai Ad Scaler |  |
| `pttagds` | [EXT-X- DISCONTINUITY- SEQUENCE](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3)タグを有効にします。 | いいえ | true — マニフェストサーバーは、送信する各m3u8ファイルのコンテンツの前にシーケンスタグを含みます。パラメーターが存在しないかtrueでない場合、マニフェストサーバーにシーケンスタグは含まれません。 |
| `pttimeline` | 広告を配置したいタイムラインとコンテンツを含む文字列。コンテンツストリーム内の広告の時間を上書きします。 | いいえ | [VODタイムライン](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md) |
| `pttoken` | TSセグメント認証トークンを有効にします。<br> **注意**:Akamai CDNトークンのみがサポートされます | TSセグメント認証トークン | ブール値 |
| `pttrackingmode` | 広告トラッキングの有効化；カスタムのクライアント側（単純型）、サーバー側(sstm)、またはハイブリッド（単純型）のいずれかです。 | いいえ | simple、sstm、simplesstm.<br> **注意**:このパラメーターを含めない場合、#EX-X-MARKERがマニフェストに挿入されます。[EXT-X-MARKERディレクティブ](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/ms-api-playlists.md)を参照してください。 |
| `pttrackingposition` | マニフェストサーバーに対して、広告トラッキング情報のみを返すように指示します。 このパラメーターはブートストラップ要求に指定しないでください。 | クライアント側のトラッキング | 英数字による注意： マニフェストサーバーは、渡された値をすべて無視します。 ただし、nullまたは空の文字列を渡すと、マニフェストサーバーはトラッキング情報ではなくM3U8を返します。 |
| `pttrackingversion` | クライアント側のトラッキング情報の形式バージョン。 | クライアント側のトラッキング | v1、v2、v3またはvmap |
| `scteTracking` | SCTEトラッキング情報をJSON V2サイドカーで取得する前に、M3U8を取得します。 <br>このパラメーターは、プレーヤーがM3U8をフェッチする際にSCTEタグ情報の取得が必要であることをマニフェストサーバーに示します。 | いいえ(デフォルト：false) | trueまたはfalse。<br> **注意**:SCTE-35データは、次のクエリパラメーター値を組み合わせたJSONサイドカーで返されます。 <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35`</li><li>`pttrackingversion=v2`</li><li>`scteTracking=true`</li></ul> |
| `vetargetmultiplier` | ライブポイントからのセグメント数プリロールオフセットは、次を使用して設定されます。`(vetargetmultiplier * targetduration + vebufferlength`<br/><br/>**注意**: ライブ/リニアのみ | いいえ(デフォルト： 3.0) | 浮動小数点 |
| `vebufferLength` | ライブポイントからの秒数。 **注意**:ライブ/リニアのみ。 | いいえ(デフォルト：3.0) | 浮動小数点 |

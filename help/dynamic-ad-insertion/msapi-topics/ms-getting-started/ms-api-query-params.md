---
description: クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、マニフェストサーバーに何を行いたいかを伝えます。 必須のものと、特定の形式や値を持つものがあります。
seo-description: クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、マニフェストサーバーに何を行いたいかを伝えます。 必須のものと、特定の形式や値を持つものがあります。
seo-title: マニフェストサーバーのクエリパラメーター
title: マニフェストサーバーのクエリパラメーター
uuid: 03632da3-ae20-427c-bd24-4794ab627cc8
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# マニフェストサーバーのクエリパラメーター {#manifest-server-query-parameters}

クエリパラメーターは、マニフェストサーバーに対して、リクエストを送信したクライアントの種類と、マニフェストサーバーに何を行いたいかを伝えます。 必須のものと、特定の形式や値を持つものがあります。

完全なURLは、ベースURLの後に疑問符が続き、引数がアンパサンドで区切ら `parameterName=value` れて構成されます。 `Base URL?name1=value1&name2=value2& . . .&name n=value n`

## 認識されるパラメータ {#section_072845B7FA94468C8068E9092983C9E6}

マニフェストサーバーは、次のパラメーターを認識します。 広告サーバーに、認識されていないすべてのパラメーターと共に、広告を処理または渡します。

| キー | 説明 | 必須 | 有効な値 |
|--- |--- |--- |--- |
| `__sid__` | マニフェストサーバーがセッションIDの生成に使用する一意のID。 | はい | 英数字 |
| g | クライアントデバイスタイプ | ターゲットルールがデバイスのタイプに依存する場合 | 「クライアントタイ [プ](https://adobeprimetime.zendesk.com) 」のリストを参照（Zendeskへのアクセスが必要） |
| k | カスタム広告ターゲット設定のキーワード | いいえ | URLセーフ文字列の形式は、key1=value1;key2=value2；です。.. |
| u | Primetime広告挿入アセットID。 | はい | MD5ハッシュ値 |
| z | アセットのPrimetime広告挿入ゾーンID。 | はい | 整数 |
| enableC3 | クライアントがC3ウィンドウ内にある。 trueの場合、ローカルで使用可能なもののみを置き換えます。それ以外の場合は、使用可能なすべてを置き換えます。 | いいえ | ブール値 |
| live | コンテンツがライブストリームかVOD（ビデオオンデマンド）ストリームかを示します。 | Akamai Ad ScalerまたはiOS Safariクライアント | ブール値 |
| パビモード | [部分的な広告ブレークの挿入のサポートを有効にする](../../msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) 。trueの場合は有効にし、falseの場合は無効にします。 | いいえ（デフォルトは無効） | start、trueまたはfalse |
| ptadwindow | 広告ステッチウィンドウの時間（秒）:DVRユーザーがストリームに参加したときに広告を検索する距離。 | いいえ（デフォルト= 1800） | 0 ～ 1800 |
| ptassetid | 発行者によって割り当てられ、管理されるコンテンツの一意のID。 | アカマイアドスケーラー | URLセーフ文字列 |
| ptcdn | トランスコードされたアセットをホストする1つ以上のCDNのリストです。 マルチCDNの [サポートを参照してください](../../creative-repackaging-service/multi-cdn-supportt.md)。 | いいえ（デフォルト=Akamai） | 例：Akamai、Level3、Limelight、Comcast |
| ptcuformat | M3U8に存在するカスタム広告キュー形式の名前。 | いいえ | DPISimple、DPIScte35、Elemental、NBC、NFLまたはTurner |
| ptfailover | マスタープレイリストで指定されたプライマリストリームとフェイルオーバーストリームを識別し、それらを別々のセットとして扱うようマニフェストサーバーに通知します。 これにより、フェイルオーバーが容易になり、タイミングエラーが発生しなくなります。 （Apple HLSデバイスのみ）。HLSプレー [ヤーの切り替えの促進を参照してくださ](../../msapi-topics/ms-insert-ads/hls-switching-to-failover.md) い。 | いいえ | true |
| ptmulticall | trueに設定した場合、FERに対する複数のAuditude広告呼び出しが行われ、広告の時間ごとに1つ。  存在しない場合、またはfalseに設定された場合、FERのauditudeに対して1つの広告呼び出しが行われます。 | いいえ | Boolean Note: 次の要件を満たしています。 <ul><li>ptcueformatパラメーターはnbcに設定する必要があります</li><li>pttimelineパラメーターは無視されます。</li></ul> |
| ptplayer | 要求を行っているプレイヤー。 | iOS/Safari | ios-mobileweb |
| 傾向 | 広告挿入によって自動生成され、Akamaiで使用されます。 追加または削除しない。 | アカマイアドスケーラー |  |
| pttagds | EXT- [X- DISCONTINUITY- SEQUENCEタグを有効にする](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3) 。 | いいえ | true — マニフェストサーバーが送信する各m3u8ファイルのコンテンツの前にシーケンスタグを含む。パラメーターが存在しないかtrueでない場合、マニフェストサーバーにシーケンスタグは含まれません。 |
| pttimeline | 広告の配置とコンテンツに必要なタイムラインを含む文字列で、コンテンツストリーム内の広告の時間を上書きします。 | いいえ | VODタイムライン( [VODタイムライン形式を参照](../../msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)) |
| pttoken | TSセグメント認証トークンを有効にする注： Akamai CDNトークンのみがサポートされます | TSセグメント認証トークン | ブール値 |
| pttrackingmode | 広告トラッキングの有効化；カスタムのクライアント側（単純型）、サーバー側（sstm型）またはハイブリッド（simplesstm型）のいずれか。 | いいえ | simple、sstmまたはsimplesstm注意： このパラメーターが含まれていない場合、#EX-X-MARKERがマニフェストに挿入されます。 EXT-X- [MARKER Directiveを参照してください](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md)。 |
| pttrackingposition | 広告追跡情報のみを返すようにマニフェストサーバーに指示します。 ブートストラップリクエストでは、このパラメーターを指定しないでください。 | クライアント側の追跡 | 英数字の注： マニフェストサーバーは、渡された値をすべて無視します。 ただし、nullまたは空の文字列を渡すと、マニフェストサーバーは追跡情報の代わりにM3U8を返します。 |
| pttrackingversion | クライアント側の追跡情報の形式バージョン。 | クライアント側の追跡 | v1、v2、v3またはvmap |
| scteTracking | SCTE追跡情報をJSON V2サイドカーで取得する前に、M3U8を取得します。  <br/>このパラメーターは、プレーヤーがM3U8を取得する際にSCTEタグ情報の取得が必要であることをマニフェストサーバーに示します。 | いいえ(デフォルト： false ) | trueまたはfalseの注意： SCTE-35データは、次のクエリパラメーター値の組み合わせと共にJSONサイドカーで返されます。 <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35` </li><li>pttrackingversion=v2 </li><li>scteTracking=true</li></ul> |
| vetargetmultiplier | ライブポイントからのセグメント数プリロールオフセットは、次を使用して設定されます。  `(  vetargetmultiplier  *  targetduration ) +  vebufferlength` 注 <br/><br/>****: ライブ/リニアのみ | いいえ(デフォルト： 3.0 ) | 浮動小数点 |
| vebufferLength | ライブポイントからの秒数注： ライブ/リニアのみ | いいえ(デフォルト： 3.0 ) | 浮動小数点 |

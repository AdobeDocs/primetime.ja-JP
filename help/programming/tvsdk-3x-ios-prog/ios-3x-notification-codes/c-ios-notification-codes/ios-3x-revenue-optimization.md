---
description: '次の表に、売上高最適化通知の詳細を示します。 '
seo-description: '次の表に、売上高最適化通知の詳細を示します。 '
seo-title: 売上高最適化コード
title: 売上高最適化コード
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# 売上高最適化コード {#revenue-optimization-code}

次の表に、売上高最適化通知の詳細を示します。

## 売上高最適化レポートの有効化 {#enable-revenue-optimization-reporting}

このレポートを有効にするには、PTMediaPlayer apiを使用します。 `[mediaPlayer
setRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

[!N注意]:ほとんどの情報通知には、ダウンロードに失敗したリソースのURLなど、関連するメタデータが含まれます。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであったかを指定するメタデータが含まれています。

|コード|名前|内部通知|メタデータキー|コメント||—|—|—|—||401001| REVENUE_OPTIMIZATION_REPORTING|なし|異なるイベントに基づくメタデータキーについては、次の表を参照してください。 |なし|

| イベントの詳細 | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** MediaPlayer::replaceCurrentResourceが呼び出されたときに、TVSDKでディスパッチされます。 | clientTimestamp、fallbackOnInvalidCreative、showStaticBanners、hasPreroll、event、adSignalingMode、resourceUrl、creativeRepackagingFormat、delayAdLoadingTolerance、zoneID、hasLivePreroll、adRequestTimeout、delayAdAdRoardingresourcetype, creativeRepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** ：コンテンツが準備済みの状態に入り、再生の準備が整ったときにTVSDKでディスパッチされます。 このイベントは、すべてのマニフェストのアップロード時にディスパッチされるわけではありません。初回の読み込み時にのみディスパッチされます。 | clientTimestamp、contentURL、contentType、event、isLive、clientID |
| **AD_OPPORTUNITY_GENERATED** ：オポチュニティが生成されたときにTVSDKでディスパッチされます。 | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** ：オポチュニティの解決が開始されたときにTVSDKでディスパッチされます。 | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** 広告リゾルバーがMediaPlayerClient::notifyFailed()を呼び出すと、TVSDKでディスパッチされます。 データの入力が必要 | opportunityId、notificationAD |
| **AD_RESOURCE_LOAD** ：広告リソースがURLで取得された場合にディスパッチされます。 responseStartTime：リクエストが最初に開始された時のUNIXタイムスタンプ。 responseTotalTime：読み込み応答に要した合計時間（秒）。 responseStatus：リソースのフェッチ中に発生したステータスコード。 ステータス：「error」または「success」リファラーAdId：このリソースのフェッチを要求した参照広告ID（存在する場合）。 referrerUrl：このリソースの取得を要求した参照URL。 errorMessage：ステータスが「error」の場合、エラーの理由はここに表示されます。 | opportunityId、resourceType、responseTotalTime、responseStatus、responseStartTime、status、errorMessage、url、referrerURL、referrerAdId |
| **AD_RESOURCE_LOAD_CRS** :CRSがアセットに適用された場合、およびm3u8の応答でTVSDK内でディスパッチされます。 resourceType:always &quot;crs&quot; responseStartTime：リクエストが最初に開始された時のUNIXタイムスタンプ。 responseTotalTime：読み込み応答に要した合計時間（秒）。 responseStatus：リソースのフェッチ中に発生したステータスコード。 ステータス：&quot;error&quot;または&quot;success&quot;。 errorMessage：ステータスが「error」の場合、エラーの理由はここに表示されます。 mediaFileUrl：選択された元のメディアファイルのURL。 mediaFileBitrate：選択されたメディアファイルのビットレート。 mediaFileMimeType:選択されたメディアファイルのMIMEタイプ。 url：最終的なアセットのURL。 | opportunityId、resourceType、responseTotalTime、responseStatus、responseStartTime、status、errorMessage、url、mediaFileURL、mediaFileBitrate、mediaFileMimeType、url |
| **AD_TIMELINE_PLACE** adBreakがタイムラインに配置された後、TVSDKでディスパッチされます。 このイベントは、広告の時間ごとに1回発生します。 proposedTime：広告の時間の配置がリクエストされた時間。 actualTime：広告の時間が実際に配置された時間。 proposedDuration：挿入を要求された広告の時間の長さ。 ライブコンテンツの場合は、キューの時間です。 VODコンテンツの場合、通常は —1です。 actualDuration：挿入される広告の時間の実際の時間。 元のストリームタイムラインで追加または置き換えられた、すべての広告の合計時間（各広告のセグメントの時間で定義）として計算されます。 proposedAds：提案された広告の時間内の広告の数。 totalAds：正常に配置された広告の数。 広告…n：広告が正常に挿入された場合は、ここに挿入されます。 広告マニフェスト全体の情報をAD_OPPORTUNITY_RESOLVE_PROCESSから取得できます。 | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, actualDuration, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** ：広告の再生開始後、TVSDKでディスパッチされます。 | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** ：広告の再生が完了した後、TVSDKでディスパッチされます。 | clientTimestamp, event, id, url, duration, type, opportunityId, clientId |
| **ADBREAK_PLAYBACK_START** TVSDKで、adbreakの再生が開始されたときにディスパッチされます。 | clientTimestamp, event, opportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** :TVSDKで、adbreakの再生が完了したときにディスパッチされます。 | clientTimestamp, event, opportunityId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** ：コンテンツが完了したときにTVSDKでディスパッチされます。これは、ストリームが置換された場合、プレイヤーがエラー状態に入った場合、プレイヤーがリセットされた場合、またはコンテンツが実際に完了した場合に発生します。 このイベントは、sessionIdを追跡するために必要です。 | clientTimestamp, event, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** ：広告の再生中にエラー（バリアントストリームエラー）が発生した場合にTVSDKでディスパッチされます。 | イベント，エラー，タイムスタンプ， manifestUrl，時間，オポチュニティID, url |
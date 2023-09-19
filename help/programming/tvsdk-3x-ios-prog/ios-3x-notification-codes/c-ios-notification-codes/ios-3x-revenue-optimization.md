---
description: この表は、収益の最適化通知の詳細を示しています。
title: 収益の最適化コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# 収益の最適化コード {#revenue-optimization-code}

この表は、収益最適化通知の詳細を示しています。

## 売上高最適化レポートを有効にする {#enable-revenue-optimization-reporting}

このレポートを有効にするには、PTMediaPlayer api を使用します。 `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>ほとんどの情報通知には、関連するメタデータ（例えば、ダウンロードに失敗したリソースの URL）が含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

| コード | 名前 | 内部通知 | メタデータキー | コメント |
|---|---|---|---|---|
| 401001 | REVENUE_OPTIMIZATION_REPORTING | なし | 以下の表で、異なるイベントに基づくメタデータキーについて説明します。 | なし |

| イベントの詳細 | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_START** MediaPlayer::replaceCurrentResource が呼び出されると、TVSDK でディスパッチされます。 | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll, event, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adLoading resourceRoadtype, creativeRepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_START** コンテンツが準備済み状態に入り、再生の準備ができた場合に TVSDK でディスパッチされます。 このイベントは、すべてのマニフェストのアップロードでディスパッチされるわけではなく、最初の読み込み時にのみディスパッチされます。 | clientTimestamp, contentURL, contentType, event, isLive, clientID |
| **AD_OPPORTUNITY_GENERATED** オポチュニティが生成されると、TVSDK でディスパッチされます。 | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_START** オポチュニティの解決が開始すると、TVSDK でディスパッチされます。 | clientTimestamp, event, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** 広告リゾルバーが MediaPlayerClient::notifyFailed() を呼び出すと、TVSDK でディスパッチされます。 データを入力する必要がある | opportunityId, notificationAD |
| **AD_RESOURCE_LOAD** URL で広告リソースが取得されるとディスパッチされます。 responseStartTime：リクエストが最初に開始した時点の UNIX タイムスタンプ。 responseTotalTime：応答の読み込みに要した合計時間（秒）。 responseStatus：リソースの取得中にステータスコードが発生しました。 status:&quot;error&quot;または&quot;success&quot; referrerAdId：このリソースの取得をリクエストした参照広告 id（存在する場合）。 referrerUrl：このリソースの取得をリクエストした参照 URL。 errorMessage：ステータスが「error」の場合、エラーの理由はここに表示されます。 | opportunityId, resourceType, resourceTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** CRS がアセットに適用された場合、および m3u8 の応答に対して TVSDK でディスパッチされます。 resourceType:always &quot;crs&quot;. responseStartTime：リクエストが最初に開始した時点の UNIX タイムスタンプ。 responseTotalTime：応答の読み込みに要した合計時間（秒）。 responseStatus：リソースの取得中にステータスコードが発生しました。 status:&quot;error&quot;または&quot;success&quot;。 errorMessage：ステータスが「error」の場合、エラーの理由はここに表示されます。 mediaFileUrl：選択された元のメディアファイルの URL。 mediaFileBitrate：選択されたメディアファイルのビットレート。 mediaFileMimeType：選択されたメディアファイルの MIME タイプ。 url：最終的なアセットの URL。 | opportunityId, resourceType, resourceTotalTime, responseStatus, responseStartTime, status, errorMessage, url, mediaFileURL, mediaFileBitrate, mediaFileMimeType, url |
| **AD_TIMELINE_PLACE** adBreak がタイムラインに配置された後、TVSDK でディスパッチされます。 このイベントは、広告ブレークごとに 1 回発生します。 proposedTime：広告ブレークの配置がリクエストされた時間。 actualTime：広告ブレークが実際に配置された時間。 proposedDuration：挿入を要求された広告ブレークの期間。 ライブコンテンツの場合は、キューの期間になります。 VOD コンテンツの場合、通常は —1 です。 actualDuration：挿入された広告ブレークの実際の期間。 元のストリームタイムラインで追加または置き換えられた、各セグメントの期間で定義された、すべての広告の合計期間として計算されます。 proposedAds：提案された広告ブレークの広告数。 totalAds：正常に配置された広告の数。 ads...n：正常に挿入された広告がここに挿入されます。 広告マニフェスト情報全体を AD_OPPORTUNITY_RESOLVE_PROCESS から取得できます | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, actualDuration, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_START** 広告の再生が開始した後、TVSDK でディスパッチされます。 | clientTimestamp，イベント， ID, URL，期間，タイプ，opportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** 広告の再生が完了した後、TVSDK でディスパッチされます。 | clientTimestamp，イベント， ID, URL，期間，タイプ，opportunityId, clientId |
| **ADBREAK_PLAYBACK_START** adbreak が再生を開始したときに TVSDK でディスパッチされます。 | clientTimestamp，イベント， opportunityId，期間，時間， clientId |
| **ADBREAK_PLAYBACK_COMPLETE** adbreak の再生が完了すると、TVSDK でディスパッチされます。 | clientTimestamp, event, opportunityId, clientId |
| **CONTENT_PLAYBACK_COMPLETE** コンテンツの完了時に TVSDK でディスパッチされます。これは、ストリームが置換された場合、プレーヤーがエラー状態になった場合、プレーヤーがリセットされた場合、またはコンテンツが実際に完了した場合に発生する可能性があります。 このイベントは、sessionId を追跡するために必要です。 | clientTimestamp，イベント， clientId, url，ステータス， errorMessage |
| **AD_PLAYBACK_ERROR** 広告の再生中にエラー（バリアントストリームエラー）が発生した場合に TVSDK でディスパッチされます。 | イベント，エラー，タイムスタンプ， manifestUrl，時間， opportunityId, url |

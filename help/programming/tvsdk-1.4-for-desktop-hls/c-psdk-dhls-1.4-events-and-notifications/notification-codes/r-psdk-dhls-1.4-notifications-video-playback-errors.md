---
description: AVEのVideo Encoderインターフェイスは、NATIVE_ERRORメタデータオブジェクトに以下のビデオ再生通知を返します。
title: NATIVE_ERRORビデオ再生値
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1339'
ht-degree: 6%

---


# NATIVE_ERROR:ビデオ再生値{#native-error-video-playback-values}

AVEのVideo Encoderインターフェイスは、NATIVE_ERRORメタデータオブジェクトに以下のビデオ再生通知を返します。

<table> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> RUNTIME_CODEメタデータキーの値 </th> 
   <th colname="col2" class="entry"> RUNTIME_CODE_MESSAGEメタデータキーの値 </th> 
   <th colname="col3" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> -1 </td> 
   <td colname="col2"><span class="codeph"> END_OF_PERIOD</span> </td> 
   <td colname="col3"> 期間の終了。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 0 </td> 
   <td colname="col2"><span class="codeph"> SUCCESS</span> </td> 
   <td colname="col3"> 操作が成功しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"> <span class="codeph"> ASYNC_OPERATION_IN_PROGRESS</span> </td> 
   <td colname="col3"> 非同期操作。 操作の要求が行われました。 成功/失敗に関する情報は、後で入手できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 2 </td> 
   <td colname="col2"><span class="codeph"> EOF</span> </td> 
   <td colname="col3"> ファイルの終了(EOF)条件が原因で、操作を実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 3 </td> 
   <td colname="col2"><span class="codeph"> DECODER_FAILED</span> </td> 
   <td colname="col3"> デコーダーが実行時に失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 4 </td> 
   <td colname="col2"><span class="codeph"> DEVICE_OPEN_ERROR</span> </td> 
   <td colname="col3"> ハードウェアデコーダーを開けませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 5 </td> 
   <td colname="col2"><span class="codeph"> FILE_NOT_FOUND  </span> </td> 
   <td colname="col3"> リソースが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 6 </td> 
   <td colname="col2"><span class="codeph"> GENERIC_ERROR  </span> </td> 
   <td colname="col3"> 一般的なエラー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 7 </td> 
   <td colname="col2"><span class="codeph"> IRRECOVERABLE_ERROR  </span> </td> 
   <td colname="col3"> ビデオエンジンが回復できないエラー状態です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 8 </td> 
   <td colname="col2"><span class="codeph"> LOST_CONNECTION_RECOVERABLE  </span> </td> 
   <td colname="col3"> ネットワークエラー。回復を試みています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 9 </td> 
   <td colname="col2"><span class="codeph"> NO_FIXED_SIZE  </span> </td> 
   <td colname="col3"> リソースのサイズを特定できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 10 </td> 
   <td colname="col2"><span class="codeph"> NOT_IMPLEMENTED  </span> </td> 
   <td colname="col3"> 機能が実装されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 11 </td> 
   <td colname="col2"><span class="codeph"> OUT_OF_MEMORY  </span> </td> 
   <td colname="col3"> メモリ不足です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 12 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR  </span> </td> 
   <td colname="col3"> メディアファイルの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 13 </td> 
   <td colname="col2"><span class="codeph"> SIZE_UNKNOWN  </span> </td> 
   <td colname="col3"> リソースのサイズは不明です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 14 </td> 
   <td colname="col2"><span class="codeph"> UNDER_FLOW  </span> </td> 
   <td colname="col3"> アンダーフロー条件。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 15 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_CONFIG  </span> </td> 
   <td colname="col3"> 構成はサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 16 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_OPERATION  </span> </td> 
   <td colname="col3"> 操作がサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 17 </td> 
   <td colname="col2"><span class="codeph"> WAITING_FOR_INIT  </span> </td> 
   <td colname="col3"> まだ初期化されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 18 </td> 
   <td colname="col2"><span class="codeph"> INVALID_PARAMETER  </span> </td> 
   <td colname="col3"> 無効なパラメータです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 19 </td> 
   <td colname="col2"><span class="codeph"> INVALID_OPERATION</span> </td> 
   <td colname="col3"> 操作が許可されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 20 </td> 
   <td colname="col2"><span class="codeph"> OP_ONLY_ALLOWED_IN_PAUSED_STATE</span> </td> 
   <td colname="col3"> 操作は一時停止中にのみ許可されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 21 </td> 
   <td colname="col2"><span class="codeph"> OP_INVALID_WITH_AUDIO_ONLY_FILE</span> </td> 
   <td colname="col3"> 操作は、オーディオ専用ファイルには使用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 22 </td> 
   <td colname="col2"><span class="codeph"> PREVIOUS_STEP_SEEK_IN_PROGRESS</span> </td> 
   <td colname="col3"> 前のシーク操作がまだ進行中です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 23 </td> 
   <td colname="col2"><span class="codeph"> SOURCE_NOT_SPECIFIED  </span> </td> 
   <td colname="col3"> リソースが指定されていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 24 </td> 
   <td colname="col2"><span class="codeph"> RANGE_ERROR</span> </td> 
   <td colname="col3"> 指定した値は範囲外です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 25 </td> 
   <td colname="col2"><span class="codeph"> INVALID_SEEK_TIME</span> </td> 
   <td colname="col3"> 無効なシーク時間です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 26 </td> 
   <td colname="col2"><span class="codeph"> FILE_STRUCTURE_INVALID</span> </td> 
   <td colname="col3"> 指定したファイルは、予期された構文に従っていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 27 </td> 
   <td colname="col2"><span class="codeph"> COMPONENT_CREATION_FAILURE</span> </td> 
   <td colname="col3"> 必須コンポーネントを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 28 </td> 
   <td colname="col2"><span class="codeph"> DRM_INIT_ERROR</span> </td> 
   <td colname="col3"> DRMコンテキストを作成できませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 29 </td> 
   <td colname="col2"><span class="codeph"> コンテナ_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> コンテナの種類がサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 30 </td> 
   <td colname="col2"><span class="codeph"> SEEK_FAILED</span> </td> 
   <td colname="col3"> シークに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 31 </td> 
   <td colname="col2"><span class="codeph"> CODEC_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> サポートされていないコーデック。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 32 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_UNAVAILABLE</span> </td> 
   <td colname="col3"> ネットワークが利用できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 33 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_ERROR</span> </td> 
   <td colname="col3"> ネットワークからのデータ取得中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 34 </td> 
   <td colname="col2"><span class="codeph"> OVERFLOW</span> </td> 
   <td colname="col3"> オーバーフロー。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 35 </td> 
   <td colname="col2"><span class="codeph"> VIDEO_プロファイル_NOT_SUPPORTED</span> </td> 
   <td colname="col3"> サポートされていないビデオプロファイル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 36 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_NOT_LOADED</span> </td> 
   <td colname="col3"> 保留期間またはまだ読み込まれていない期間に操作が試行されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 37 </td> 
   <td colname="col2"><span class="codeph"> INVALID_REPLACE_DURATION</span> </td> 
   <td colname="col3"> 指定した置き換え期間が無効か、ストリームの終わりを超えています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 38 </td> 
   <td colname="col2"><span class="codeph"> CALLED_FROM_WRONG_THREAD</span> </td> 
   <td colname="col3"> APIを間違ったスレッドから呼び出すことはできません。 ほとんどの場合、APIエレメントはメインスレッドからのみ呼び出す必要があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 39 </td> 
   <td colname="col2"><span class="codeph"> FRAGMENT_READ_ERROR</span> </td> 
   <td colname="col3"> フラグメント読み取りエラー。 フェールオーバーが存在しません。 エンジンは次のフラグメントの読み取りを試みます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 40 </td> 
   <td colname="col2"><span class="codeph"> ABORTED</span> </td> 
   <td colname="col3"> 明示的なAbortまたはDestroyの呼び出しによって、操作が中止されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 41 </td> 
   <td colname="col2"><span class="codeph"> UNSUPPORTED_HLS_VERSION</span> </td> 
   <td colname="col3"> このバージョンのHLSメディアは再生できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 42 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_FAIL_OVER</span> </td> 
   <td colname="col3"> フェイルオーバーできません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 43 </td> 
   <td colname="col2"><span class="codeph"> HTTP_TIME_OUT</span> </td> 
   <td colname="col3"> HTTPダウンロードがタイムアウトしました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 44 </td> 
   <td colname="col2"><span class="codeph"> NETWORK_DOWN  </span> </td> 
   <td colname="col3"> ユーザーのネットワーク接続がダウンしています。 いつでも再生が停止する可能性があり、接続が利用可能になると再開します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 45 </td> 
   <td colname="col2"><span class="codeph"> NO_USABLE_BITRATE_プロファイル</span> </td> 
   <td colname="col3"> 使用可能なビットレートプロファイルがストリームに見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 46 </td> 
   <td colname="col2"><span class="codeph"> BAD_MANIFEST_SIGNATURE</span> </td> 
   <td colname="col3"> マニフェストに不正な署名があります。 マニフェストの署名テストに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 47 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_LOAD_PLAYLIST</span> </td> 
   <td colname="col3"> プレイリストを読み込めません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 48 </td> 
   <td colname="col2"><span class="codeph"> REPLACEMENT_FAILED</span> </td> 
   <td colname="col3"> 挿入APIで指定された置き換えに失敗しました。 これは、挿入に成功したが置き換えに失敗したことを意味します。 置き換えるマニフェストがタイムラインから削除されていると、置き換えに失敗する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 49 </td> 
   <td colname="col2"><span class="codeph"> SWITCH_TO_ASYMMETRIC_プロファイル</span> </td> 
   <td colname="col3"> DRMが非対称プロファイルに切り替わっています。 すべてのプロファイルは期間内に整列する必要があります。 そうでない場合は、この警告がスローされ、再生が飛ぶことがあります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 50 </td> 
   <td colname="col2"><span class="codeph"> LIVE_WINDOW_MOVED_BACKWARD</span> </td> 
   <td colname="col3"> ライブウィンドウは次に進むだけでよいと想定されています。 そうでない場合は、この警告がスローされ、ウィンドウは読み取られません。 そのため、再生が飛ぶ（または停止/長い一時停止）場合があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 51 </td> 
   <td colname="col2"><span class="codeph"> CURRENT_PERIOD_EXPIRED</span> </td> 
   <td colname="col3"> ライブウィンドウが現在の期間を超えました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 52 </td> 
   <td colname="col2"><span class="codeph"> CONTENT_LENGTH_MISMATCH</span> </td> 
   <td colname="col3"> HTTPサーバーから報告されるコンテンツの長さが、実際のメディアサイズと一致しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 53 </td> 
   <td colname="col2"><span class="codeph"> PERIOD_HOLD</span> </td> 
   <td colname="col3"> <span class="codeph"> setHoldAt</span> APIで設定された時間に達したため、メディアリーダーはこれ以上読み取れません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 54 </td> 
   <td colname="col2"><span class="codeph"> LIVE_HOLD  </span> </td> 
   <td colname="col3"> ライブウィンドウの終わりに達したので、メディアリーダーはセグメントを読み込めません。 サーバーがライブウィンドウに新しいメディアを広告すると、セグメントの読み込みが再開されます。 この状態は、通常、次の場合に達します。 
    <ul id="ul_FCFF658EDA4144E59970B317D6DEB624"> 
     <li id="li_2F6EEEB782D54CD999BC7CC7C0B78B48"><span class="codeph"> bufferTime</span>が高すぎます（ライブ時間の長さ以上）。 </li> 
     <li id="li_25CE97115ED64E44AA89977FB5F0DCF7">1つ以上の挿入/消去APIの組み合わせにより、追加されたメディアより多くのメディアが置き換えられました。 </li> 
     <li id="li_1B14716B2157492AB1859306D1250523">次の期間は、メディアの置き換えが保留中のライブ期間です（<span class="codeph"> InsertBy</span> APIの呼び出しが原因） </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 55 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_INTERLEAVING  </span> </td> 
   <td colname="col3"> メディアのオーディオとビデオが正しくインターリーブされません。 これはパッケージ化エラーです。 この警告は、差が2秒を超えると発行されます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 56 </td> 
   <td colname="col2"><span class="codeph"> DRM_NOT_AVAILABLE</span> </td> 
   <td colname="col3"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 57 </td> 
   <td colname="col2"><span class="codeph"> PLAYBACK_NOT_AUTHORIZED</span> </td> 
   <td colname="col3"> Flash PlayerでHLS再生が有効になっていません。 <span class="codeph"> AuthorizedFeatures.enableHLSPlayback</span>を参照してください。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 58 </td> 
   <td colname="col2"><span class="codeph"> BAD_MEDIA_SAMPLE_FOUND</span> </td> 
   <td colname="col3"> デコーダーが、デコードできない不正なサンプルを受け取りました。 通常、これは致命的なエラーではありませんが、オーディオ/ビデオに問題がある可能性を示しています。 このエラーのインスタンスが多すぎる場合は、不正なエンコードまたは不正なファイルを示しています。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 59 </td> 
   <td colname="col2"><span class="codeph"> RANGE_SPANS_READ_HEAD</span> </td> 
   <td colname="col3"> 再生が開始した後は、挿入/置換範囲に読み取りヘッドが含まれていてはなりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 60 </td> 
   <td colname="col2"><span class="codeph"> POSTROLL_WITH_LIVE_NOT_ALLOWED</span> </td> 
   <td colname="col3"> ポストロール挿入は、ライブメディアでは使用できません。 ただし、サーバーがメディアを完了とマークした後でも使用できます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 61 </td> 
   <td colname="col2"><span class="codeph"> INTERNAL_ERROR</span> </td> 
   <td colname="col3"> 非常にまれな問題であり、常に発生しないはずです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 62 </td> 
   <td colname="col2"><span class="codeph"> SPS_PPS_FOUND_OUTSIDE_AVCC</span> </td> 
   <td colname="col3"> ストリームが、パッケージ化の推奨に従わず、常にH264 SPS/PPSをAVCCに含める。 シーク/再生に関する問題が表示される場合があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 63 </td> 
   <td colname="col2"><span class="codeph"> PARTIAL_REPLACEMENT</span> </td> 
   <td colname="col3"> 挿入APIで指定された置き換えは部分的にしか行われませんでした。 replaceDurationがタイムライン期間に及んでいる場合に発生します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 64 </td> 
   <td colname="col2"><span class="codeph"> RENDITION_M3U8_ERROR</span> </td> 
   <td colname="col3"> レンディションプレイリストで読み込み中にエラーが発生しました。 これはAVEに対してのみ有効で、FlashPlayerには適用されません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 65 </td> 
   <td colname="col2"><span class="codeph"> NULL_OPERATION</span> </td> 
   <td colname="col3"> 操作は何も実行しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 66 </td> 
   <td colname="col2"><span class="codeph"> SEGMENT_SKIPPED_ON_FAILURE</span> </td> 
   <td colname="col3"> セグメントは再生できず、失敗した場合はスキップされます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 67 </td> 
   <td colname="col2"><span class="codeph"> INCOMPATIBLE_RENDER_MODE</span> </td> 
   <td colname="col3"> 非互換のレンダリングモード。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 68 </td> 
   <td colname="col2"><span class="codeph"> PROTOCOL_NOT_SUPPORTED  </span> </td> 
   <td colname="col3"> URLで使用されるWebプロトコルはサポートされていません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 69 </td> 
   <td colname="col2"><span class="codeph"> PARSE_ERROR_INCOMPATIBLE_VERSION</span> </td> 
   <td colname="col3"> メディアファイルの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 70 </td> 
   <td colname="col2"><span class="codeph"> MANIFEST_FILE_UNEXPECTEDLY_CHANGED</span> </td> 
   <td colname="col3"> マニフェストファイルが予期しない方法で変更されました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 71 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_SPLIT_TIMELINE</span> </td> 
   <td colname="col3"> 分割操作をタイムラインで実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 72 </td> 
   <td colname="col2"><span class="codeph"> CANNOT_ERASE_TIMELINE</span> </td> 
   <td colname="col3"> 消去操作をタイムラインで実行できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 73 </td> 
   <td colname="col2"><span class="codeph"> DID_NOT_GET_NEXT_FRAGMENT</span> </td> 
   <td colname="col3"> 次のフラグメントを取得しませんでした。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 74 </td> 
   <td colname="col2"><span class="codeph"> NO_TIMELINE</span> </td> 
   <td colname="col3"> 内部データ構造にタイムラインがありません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 75 </td> 
   <td colname="col2"><span class="codeph"> LISTENER_NOT_FOUND</span> </td> 
   <td colname="col3"> 内部データ構造にリスナーが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 76 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_開始_ERROR</span> </td> 
   <td colname="col3"> オーディオを開始できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 77 </td> 
   <td colname="col2"><span class="codeph"> NO_AUDIO_SINK</span> </td> 
   <td colname="col3"> 内部データ構造にオーディオシンクがありません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 78 </td> 
   <td colname="col2"><span class="codeph"> FILE_OPEN_ERROR</span> </td> 
   <td colname="col3"> ファイルを開けません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 79 </td> 
   <td colname="col2"><span class="codeph"> FILE_WRITE_ERROR</span> </td> 
   <td colname="col3"> ファイルに書き込めません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 80 </td> 
   <td colname="col2"><span class="codeph"> FILE_READ_ERROR</span> </td> 
   <td colname="col3"> ファイルから読み取れません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 81 </td> 
   <td colname="col2"><span class="codeph"> ID3PARSE_ERROR</span> </td> 
   <td colname="col3"> ID3データの解析中にエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 82 </td> 
   <td colname="col2"><span class="codeph"> SECURITY_ERROR  </span> </td> 
   <td colname="col3"> セキュリティ上の制約により、コンテンツの読み込みに失敗しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 83 </td> 
   <td colname="col2"><span class="codeph"> TIMELINE_TOO_SHORT</span> </td> 
   <td colname="col3"> タイムラインの時間が短すぎます。 これがライブストリームの場合、バッファリングが頻繁に発生する可能性があります。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 84 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_開始</span> </td> 
   <td colname="col3"> ストリームがオーディオ専用ストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 85 </td> 
   <td colname="col2"><span class="codeph"> AUDIO_ONLY_STREAM_END</span> </td> 
   <td colname="col3"> ストリームがオーディオ専用からビデオ付きストリームに切り替えられました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 87 </td> 
   <td colname="col2"><span class="codeph"> KEY_NOT_FOUND  </span> </td> 
   <td colname="col3"> キーが見つかりません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 88 </td> 
   <td colname="col2"><span class="codeph"> INVALID_KEY</span> </td> 
   <td colname="col3"> キーが無効です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 89 </td> 
   <td colname="col2"> <span class="codeph"> KEY_SERVER_NOT_FOUND</span> </td> 
   <td colname="col3"> キーサーバーはキーを返しません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 90 </td> 
   <td colname="col2"> <span class="codeph"> MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</span> </td> 
   <td colname="col3"> メインマニフェストの更新を処理できません。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 91 </td> 
   <td colname="col2"> <span class="codeph"> UNREPORTED_TIME_DISCONTINUITY_FOUND</span> </td> 
   <td colname="col3"> 報告されない時間(PTS)不連続が見つかりました。 </td> 
  </tr> 
 </tbody> 
</table>


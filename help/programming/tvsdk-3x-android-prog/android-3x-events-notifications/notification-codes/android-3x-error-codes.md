---
title: PSDK エラーコード
description: 様々なエラーコード、警告およびネイティブエラーコードに関する情報です。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 6%

---

# PSDK エラーコード {#psdk-error-codes}

PSDK のエラーコード、警告およびネイティブエラーコードについて説明します。

## エラー

次の表に、ERROR タイプの通知の詳細を示します。 ほとんどのエラーには、関連するメタデータ（例えば、ダウンロードに失敗したリソースの URL）が含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1">
  <tr> 
   <th><b>PSDK エラー名</b></th>
   <th><b>PSDK エラーコード</b></th>
   <th><b>説明</b></th>
  </tr>
  <tr>
    <td>成功</td>
    <td>0</td>
    <td>基になる API が実行した操作が成功しました。</td>
  </tr>
  <tr>
    <td>INVALID_ARGUMENT</td>
    <td>1</td>
    <td>基になる API に指定された引数のデータまたは形式が無効です。</td>
  </tr>
  <tr>
    <td>NULL_POINTER</td>
    <td>2</td>
    <td>渡された引数の 1 つが NULL であるか、内部メンバの 1 つが初期化されませんでした。</td>
  </tr>
  <tr>
    <td>ILLEGAL_STATE</td>
    <td>3</td>
    <td>この操作は、現在のプレーヤーの状態ではサポートされていません。</td>
  </tr>
  <tr>
    <td>INTERFACE_NOT_FOUND</td>
    <td>4</td>
    <td>interfaceCast メソッドは、要求されたインターフェイスがこのメソッドによって実装または継承されない場合に、このエラーをスローします。</td>
  </tr>
  <tr>  
    <td>CREATION_FAILED</td>
    <td>5</td>
    <td>内部リソースの 1 つを作成できませんでした。</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_OPERATION</td>
    <td>6</td>
    <td>リクエストされた操作は現在サポートされていません。</td>
  </tr>
  <tr>
    <td>DATA_NOT_AVAILABLE</td>
    <td>7</td>
    <td>リクエストされたデータは現在使用できません。</td>
  </tr>
  <tr>
    <td>SEEK_ERROR</td>
    <td>8</td>
    <td>シーク操作の実行中にエラーが発生しました。</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_FEATURE</td>
    <td>9</td>
    <td>この機能はサポートされていません。</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>10</td>
    <td>指定された値は範囲外です。</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>11</td>
    <td>指定されたストリームのオーディオ/ビデオコーデックは、TVSDK または基になるデバイスではサポートされていません。</td>
  </tr>
  <tr>
    <td>MEDIA_ERROR</td>
    <td>12</td>
    <td>指定されたメディアが見つかりません。</td>
  </tr>
  <tr>
    <td>NETWORK_ERROR</td>
    <td>13</td>
    <td>フラグメントまたはセグメント（ビデオとオーディオの両方）のダウンロード中にエラーが発生しました。</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>14</td>
    <td>汎用エラーイベント。 TVSDK が実際に発行したものではありません。 これは、 TVSDK エラーイベントに対応する数値コードの範囲の終わりのマーカーに過ぎません。</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>15</td>
    <td>指定されたシーク時間が無効です。</td>
  </tr>
  <tr>
    <td>AUDIO_TRACK_ERROR</td>
    <td>16</td>
    <td>オーディオトラックに関連するエラーが発生しました（代替オーディオ）</td>
  </tr>
  <tr>
    <td>ACCESS_FROM_DIFFERENT_THREAD</td>
    <td>17</td>
    <td>PSDK API は、PSDK が初期化されたスレッドとは異なるスレッドから呼び出されます。</td>
  </tr>
  <tr>
    <td>ELEMENT_NOT_FOUND</td>
    <td>18</td>
    <td>要素が見つかりません。</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>19</td>
    <td>機能が実装されていません。</td>
  </tr>
  <tr>
    <td>PRE_ROLL_DISABLED</td>
    <td>20</td>
    <td>プリロールは AdvertisingMetadata を介して無効になっています。</td>
  </tr>
  <tr>
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>Flash Playerで HLS 再生が有効になっていません。 AuthorizedFeatures.enableMediaPlayerHLSPlayback() を参照してください。</td>
  </tr>
  <tr>
    <td>NETWORK_TIMEOUT</td>
    <td>58</td>
    <td>リソース/接続サーバーの取得中にネットワークがタイムアウトしました。</td>
  </tr>
</table>

## 警告

次の表に、WARN タイプの通知の詳細を示します。
ほとんどの警告には、ダウンロードに失敗したリソースの URL など、関連するメタデータが含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>エラー名</b></th>
    <th><b>コード</b></th>
    <th><b>説明</b></th>
  </tr>
  <tr>
    <td>PLAYBACK_OPERATION_FAILED</td>
    <td>200</td>
    <td>再生操作中にエラーが発生しました。 再生関連の操作が失敗しました</td>
  </tr>
  <tr>  
    <td>NATIVE_WARNING</td>
    <td>201</td>
    <td>低レベルの AVE ライブラリがエラーを発行しました。</td>
  </tr>
  <tr>
    <td>AD_RESOLVER_FAILED</td>
    <td>202</td>
    <td>広告プラグインが広告を解決できませんでした。</td>
  </tr>
  <tr>
    <td>AD_MANIFEST_LOAD_FAILED</td>
    <td>203</td>
    <td>広告マニフェストを読み込めませんでした。</td>
  </tr>
  <tr>
    <td>AD_RESOLUTION_IN_PROGRESS</td>
    <td>204</td>
    <td>広告の解決の操作が進行中です。</td>
  </tr>
  </table>

## 情報

<table frame="all" colsep="1" rowsep="1">
  <tr> 
    <th><b>エラー名</b></th>
    <th><b>コード</b></th>
    <th><b>説明</b></th>
  </tr>
  <tr>
    <td>REVENUE_OPTIMIZATION_REPORTING</td>
    <td>300</td>
    <td>TVSDK 詳細な通知を参照してください。</td>
  </tr>
 </table>

## ネイティブエラーコード

AVE の Video Encoder インターフェイスは、NATIVE_ERROR メタデータオブジェクトに次のビデオ再生通知を返します。

<table frame="all" colsep="1" rowsep="1">
  <tr>
    <th><b>エラー名</b></th>
    <th><b>コード</b></th>
    <th><b>説明</b></th>
  </tr>
  <tr>  
    <td>END_OF_PERIOD</td>
    <td>-1</td>
    <td>期間の終わり。</td>
  </tr>
  <tr>
    <td>成功</td>
    <td>0</td>
    <td>操作に成功しました。</td>
  </tr>
  <tr>
    <td>ASYNC_OPERATION_IN_PROGRESS</td>
    <td>1</td>
    <td>非同期操作。 操作リクエストが実行されました。 成功/失敗に関する情報は、後で入手できます。</td>
  </tr>
  <tr>
    <td>EOF</td>
    <td>2</td>
    <td>ファイルの終了 (EOF) 条件が原因で、操作ができません。</td>
  </tr>
  <tr>
    <td>DECODER_FAILED</td>
    <td>3</td>
    <td>実行時にデコーダーが失敗しました。</td>
  </tr>
  <tr>
    <td>DEVICE_OPEN_ERROR</td>
    <td>4</td>
    <td>ハードウェアデコーダーを開けませんでした。</td>
  </tr>
  <tr>
    <td>FILE_NOT_FOUND</td>
    <td>5</td>
    <td>リソースが見つかりません。</td>
  </tr>
  <tr>
    <td>GENERIC_ERROR</td>
    <td>6</td>
    <td>一般的なエラーです。</td>
  </tr>
  <tr>
    <td>IRRECOVERABLE_ERROR</td>
    <td>7</td>
    <td>ビデオエンジンが復元できないエラー状態。</td>
  </tr>
  <tr>
    <td>LOST_CONNECTION_RECOVERABLE</td>
    <td>8</td>
    <td>ネットワークエラー。復元を試みています。</td>
  </tr>
  <tr> 
    <td>NO_FIXED_SIZE</td>
    <td>9</td>
    <td>リソースのサイズを決定できません。</td>
  </tr>
  <tr>
    <td>NOT_IMPLEMENTED</td>
    <td>10</td>
    <td>機能が実装されていません。</td>
  </tr>
  <tr>
    <td>OUT_OF_MEMORY</td>
    <td>11</td>
    <td>メモリ不足です。</td>
  </tr>
  <tr>
    <td>PARSE_ERROR</td>
    <td>12</td>
    <td>メディアファイルの解析中にエラーが発生しました。</td>
  </tr>
  <tr>  
    <td>SIZE_UNKNOWN</td>
    <td>13</td>
    <td>リソースのサイズが不明です。</td>
  </tr>
  <tr>  
    <td>UNDER_FLOW</td>
    <td>14</td>
    <td>アンダーフロー条件。</td>
  </tr>
  <tr> 
    <td>UNSUPPORTED_CONFIG</td>
    <td>15</td>
    <td>設定はサポートされていません。</td>
  </tr>
  <tr>  
    <td>UNSUPPORTED_OPERATION</td>
    <td>16</td>
    <td>操作はサポートされていません。</td>
  </tr>
  <tr>
    <td>WAITING_FOR_INIT</td>
    <td>17</td>
    <td>まだ初期化されていません。</td>
  </tr>
  <tr>  
    <td>INVALID_PARAMETER</td>
    <td>18</td>
    <td>無効なパラメーターです。</td>
  </tr>
  <tr>
    <td>INVALID_OPERATION</td>
    <td>19</td>
    <td>操作が許可されていません。</td>
  </tr>
  <tr>
    <td>OP_ONLY_ALLOWED_IN_PAUSED_STATE</td>
    <td>20</td>
    <td>この操作は、一時停止中にのみ許可されます。</td>
  </tr>
  <tr> 
    <td>OP_INVALID_WITH_AUDIO_ONLY_FILE</td>
    <td>21</td>
    <td>オーディオ専用ファイルでは操作を使用できません。</td>
  </tr>
  <tr>
    <td>PREVIOUS_STEP_SEEK_IN_PROGRESS</td>
    <td>22</td>
    <td>前のシーク操作は、まだ進行中です。</td>
  </tr>
  <tr> 
    <td>SOURCE_NOT_SPECIFIED</td>
    <td>23</td>
    <td>リソースが指定されていません。</td>
  </tr>
  <tr>
    <td>RANGE_ERROR</td>
    <td>24</td>
    <td>指定された値は範囲外です。</td>
  </tr>
  <tr>
    <td>INVALID_SEEK_TIME</td>
    <td>25</td>
    <td>シーク時間が無効です。</td>
  </tr>
  <tr>
    <td>FILE_STRUCTURE_INVALID</td>
    <td>26</td>
    <td>指定されたファイルは、想定される構文に従っていません。</td>
  </tr>
  <tr>
    <td>COMPONENT_CREATION_FAILURE</td>
    <td>27</td>
    <td>必須コンポーネントを作成できませんでした。</td>
  </tr>
  <tr>
    <td>DRM_INIT_ERROR</td>
    <td>28</td>
    <td>DRM コンテキストを作成できませんでした。</td>
  </tr>
  <tr>
    <td>CONTAINER_NOT_SUPPORTED</td>
    <td>29</td>
    <td>コンテナタイプはサポートされていません。</td>
  </tr>
  <tr>
    <td>SEEK_FAILED</td>
    <td>30</td>
    <td>シークに失敗しました。</td>
  </tr>
  <tr>
    <td>CODEC_NOT_SUPPORTED</td>
    <td>31</td>
    <td>サポートされていないコーデック。</td>
  </tr>
  <tr>
    <td>NETWORK_UNAVAILABLE</td>
    <td>32</td>
    <td>ネットワークが使用できません。</td>
  </tr>
  <tr>  
    <td>NETWORK_ERROR</td>
    <td>33</td>
    <td>ネットワークからデータを取得中にエラーが発生しました。</td>
  </tr>
  <tr>
    <td>OVERFLOW</td>
    <td>34</td>
    <td>オーバーフロー。</td>
  </tr>
  <tr>  
    <td>VIDEO_PROFILE_NOT_SUPPORTED</td>
    <td>35</td>
    <td>サポートされていないビデオプロファイル。</td>
  </tr>
  <tr>
    <td>PERIOD_NOT_LOADED</td>
    <td>36</td>
    <td>HOLD 期間またはまだ読み込まれていない期間に対して操作が試行されました。</td>
  </tr>
  <tr> 
    <td>INVALID_REPLACE_DURATION</td>
    <td>37</td>
    <td>指定した置き換え期間が無効か、ストリームの終わりを超えています。</td>
  </tr>
  <tr>
    <td>CALLED_FROM_WRONG_THREAD</td>
    <td>38</td>
    <td>間違ったスレッドから API を呼び出すことはできません。 主に、API 要素はメインスレッドからのみ呼び出す必要があります。</td>
  </tr>
  <tr>
    <td>FRAGMENT_READ_ERROR</td>
    <td>39</td>
    <td>フラグメントの読み取りエラー。 フェールオーバーが存在しません。 エンジンは次のフラグメントを読み取ろうとします。</td>
  </tr>
  <tr>
    <td>中止</td>
    <td>40</td>
    <td>操作は、明示的な Abort または Destroy の呼び出しによって中止されました。</td>
  </tr>
  <tr>
    <td>UNSUPPORTED_HLS_VERSION</td>
    <td>41</td>
    <td>このバージョンの HLS メディアを再生できません。</td>
  </tr>
  <tr>
    <td>CANNOT_FAIL_OVER</td>
    <td>42</td>
    <td>フェイルオーバーできません。</td>
  </tr>
  <tr> 
    <td>HTTP_TIME_OUT</td>
    <td>43</td>
    <td>HTTP ダウンロードがタイムアウトしました。</td>
  </tr>
  <tr>
    <td>NETWORK_DOWN</td>
    <td>44</td>
    <td>ユーザーのネットワーク接続がダウンしています。 再生はいつでも停止する可能性があり、接続が利用可能になると再開します。</td>
  </tr>
  <tr>
    <td>NO_USABLE_BITRATE_PROFILE</td>
    <td>45</td>
    <td>使用可能なビットレートプロファイルがストリームに見つかりません。</td>
  </tr>
  <tr>
    <td>BAD_MANIFEST_SIGNATURE</td>
    <td>46</td>
    <td>マニフェストに無効な署名があります。 マニフェストの署名テストに失敗しました。</td>
  </tr>
  <tr>
    <td>CANNOT_LOAD_PLAYLIST</td>
    <td>47</td>
    <td>プレイリストを読み込めません。</td>
  </tr>
  <tr>
    <td>REPLACEMENT_FAILED</td>
    <td>48</td>
    <td>挿入 API で指定された置換は成功しませんでした。 これは、挿入が成功したが置き換えが成功しなかったことを意味します。 置き換えるマニフェストがタイムラインから削除されている場合、置き換えに失敗する可能性があります。</td>
  </tr>
  <tr>
    <td>SWITCH_TO_ASYMMETRIC_PROFILE</td>
    <td>49</td>
    <td>DRM が非対称プロファイルに切り替え中です。 すべてのプロファイルは、期間内に整列する必要があります。 そうでない場合は、この警告がスローされ、再生にジャンプが発生する場合があります。</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_BACKWARD</td>
    <td>50</td>
    <td>ライブウィンドウは前に進むことのみが想定されています。 そうでない場合は、この警告がスローされ、ウィンドウは読み取られません。 そのため、再生にジャンプ（または停止/長い一時停止）が発生する場合があります。</td>
  </tr>
  <tr>
    <td>CURRENT_PERIOD_EXPIRED</td>
    <td>51</td>
    <td>ライブウィンドウが現在の期間を超えました。</td>
  </tr>
  <tr>
    <td>CONTENT_LENGTH_MISMATCH</td>
    <td>52</td>
    <td>HTTP サーバーから報告された content-length が、実際のメディアサイズと一致しませんでした。</td>
  </tr>
  <tr>
    <td>PERIOD_HOLD</td>
    <td>53</td>
    <td>setHoldAt API で設定された時間に達したので、メディアリーダーはこれ以上読み取れません。</td>
  </tr>
  <tr>  
    <td>LIVE_HOLD</td>
    <td>54</td>
    <td>ライブウィンドウの終わりに達したので、メディアリーダーはセグメントを読み込めません。 サーバーがライブウィンドウに新しいメディアを追加すると、セグメントの読み込みが再開されます。 通常、この状態になるのは、次の場合です。<ul><li>bufferTime が長すぎます（ライブウィンドウの時間以上）。</li><li>1 つ以上の挿入/消去 API の組み合わせにより、追加されたメディアより多くのメディアが置き換えられました。</li><li>次の期間は、（InsertBy API 呼び出しによる）保留中のメディア置き換えを含むライブ期間です。</li></ul></td>
  </tr>
  <tr>
    <td>BAD_MEDIA_INTERLEAVING</td>
    <td>55</td>
    <td>メディアのオーディオおよびビデオのインターリービングが正しく行われません。 これはパッケージ化エラーです。 この警告は、差が 2 秒を超えるとディスパッチされます。</td>
  </tr>
  <tr>
    <td>DRM_NOT_AVAILABLE</td>
    <td>56</td>
    <td></td>
  </tr>
  <tr>  
    <td>PLAYBACK_NOT_AUTHORIZED</td>
    <td>57</td>
    <td>Flash Playerで HLS 再生が有効になっていません。 AuthorizedFeatures.enableHLSPlayback を参照してください。</td>
  </tr>
  <tr>
    <td>BAD_MEDIA_SAMPLE_FOUND</td>
    <td>58</td>
    <td>デコーダーは、デコードできない不正なサンプルを受信しました。 これは通常、致命的なエラーではありませんが、オーディオ/ビデオに問題が発生している可能性があることを示しています。 このエラーのインスタンスが多すぎる場合は、エンコーディングが正しくないか、ファイルが正しくありません。</td>
  </tr>
  <tr>
    <td>RANGE_SPANS_READ_RANGEHEAD</td>
    <td>59</td>
    <td>再生が開始した後、挿入/置換範囲に読み取りヘッドが含まれていない必要があります。</td>
  </tr>
  <tr> 
    <td>POSTROLL_WITH_LIVE_NOT_ALLOWED</td>
    <td>60</td>
    <td>ポストロール挿入は、ライブメディアでは使用できません。 ただし、サーバーがメディアを完了とマークした後で使用できます。</td>
  </tr>
  <tr>
    <td>INTERNAL_ERROR</td>
    <td>61</td>
    <td>発生しないべきでない非常にまれな問題です。</td>
  </tr>
  <tr>  
    <td>SPS_PPS_FOUND_OUTSIDE_AVCC</td>
    <td>62</td>
    <td>ストリームは、H264 SPS/PPS を常に AVCC に配置するというパッケージ化の推奨に従っていません。 シーク/再生の問題が発生する可能性があります。</td>
  </tr>
  <tr>  
    <td>PARTIAL_REPLACEMENT</td>
    <td>63</td>
    <td>Insert API で指定された置換は部分的にのみ行われました。 この処理は、 replaceDuration がタイムライン期間にわたってまたがる場合に発生します。</td>
  </tr>
  <tr>
    <td>RENDITION_M3U8_ERROR</td>
    <td>64</td>
    <td>レンディションプレイリストの読み込み中にエラーが発生しました。 これは AVE に対してのみ使用され、FlashPlayer に対しては使用されません。</td>
  </tr>
  <tr>
    <td>NULL_OPERATION</td>
    <td>65</td>
    <td>操作で何も実行されません。</td>
  </tr>
  <tr>
    <td>SEGMENT_SKIPPED_ON_FAILURE</td>
    <td>66</td>
    <td>セグメントは再生できず、失敗した場合はスキップされます。</td>
  </tr>
  <tr>
    <td>INCOMPATIBLE_RENDER_MODE</td>
    <td>67</td>
    <td>非互換のレンダリングモードです。</td>
  </tr>
  <tr>
    <td>PROTOCOL_NOT_SUPPORTED</td>
    <td>68</td>
    <td>この URL で使用される Web プロトコルはサポートされていません。</td>
  </tr>
  <tr>
    <td>PARSE_ERROR_INCOMPATIBLE_VERSION</td>
    <td>69</td>
    <td>メディアファイルの解析中にエラーが発生しました。</td>
  </tr>
  <tr>  
    <td>MANIFEST_FILE_UNEXPECTEDLY_CHANGED</td>
    <td>70</td>
    <td>マニフェストファイルが予期しない方法で変更されました。</td>
  </tr>
  <tr>
    <td>CANNOT_SPLIT_TIMELINE</td>
    <td>71</td>
    <td>タイムラインで分割操作を実行できません。</td>
  </tr>
  <tr>
    <td>CANNOT_ERASE_TIMELINE</td>
    <td>72</td>
    <td>タイムラインで消去操作を実行できません。</td>
  </tr>
  <tr>
    <td>DID_NOT_GET_NEXT_FRAGMENT</td>
    <td>73</td>
    <td>次のフラグメントを取得しませんでした。</td>
  </tr>
  <tr>
    <td>NO_TIMELINE</td>
    <td>74</td>
    <td>内部データ構造にタイムラインが存在しません。</td>
  </tr>
  <tr>
    <td>LISTENER_NOT_FOUND</td>
    <td>75</td>
    <td>内部データ構造にリスナーが見つかりません。</td>
  </tr>
  <tr>
    <td>AUDIO_START_ERROR</td>
    <td>76</td>
    <td>オーディオを開始できません。</td>
  </tr>
  <tr>
    <td>NO_AUDIO_SINK</td>
    <td>77</td>
    <td>内部データ構造にオーディオシンクがありません。</td>
  </tr>
  <tr>  
    <td>FILE_OPEN_ERROR</td>
    <td>78</td>
    <td>ファイルを開けません。</td>
  </tr>
  <tr>
    <td>FILE_WRITE_ERROR</td>
    <td>79</td>
    <td>ファイルに書き込めません。</td>
  </tr>
  <tr>
    <td>FILE_READ_ERROR</td>
    <td>80</td>
    <td>ファイルから読み取れません。</td>
  </tr>
  <tr>
    <td>ID3PARSE_ERROR</td>
    <td>81</td>
    <td>ID3 データの解析中にエラーが発生しました。</td>
  </tr>
  <tr>
    <td>SECURITY_ERROR</td>
    <td>82</td>
    <td>セキュリティ上の制限により、コンテンツの読み込みに失敗しました。</td>
  </tr>
  <tr>
    <td>TIMELINE_TOO_SHORT</td>
    <td>83</td>
    <td>タイムラインの期間が短すぎます。 ライブストリームの場合は、バッファリングが頻繁に発生する可能性があります。</td>
  </tr>
  <tr>
    <td>AUDIO_ONLY_STREAM_START</td>
    <td>84</td>
    <td>ストリームがオーディオ専用ストリームに切り替えられました。</td>
  </tr>
  <tr>  
    <td>AUDIO_ONLY_STREAM_END</td>
    <td>85</td>
    <td>ストリームがオーディオのみからビデオ付きストリームに切り替えられました。</td>
  </tr>
  <tr>
    <td>KEY_NOT_FOUND</td>
    <td>87</td>
    <td>キーが見つかりません。</td>
  </tr>
  <tr>
    <td>INVALID_KEY</td>
    <td>88</td>
    <td>キーが無効です。</td>
  </tr>
  <tr>
    <td>KEY_SERVER_NOT_FOUND</td>
    <td>89</td>
    <td>キーサーバーはキーを返しません。</td>
  </tr>
  <tr>
    <td>MAIN_MANIFEST_UPDATE_TO_BE_HANDLED</td>
    <td>90</td>
    <td>メインのマニフェストの更新を処理できません。</td>
  </tr>
  <tr>
    <td>UNREPORTED_TIME_DISCONTINUITY_FOUND</td>
    <td>91</td>
    <td>報告されていない時間 (PTS) 不連続が見つかりました。</td>
  </tr>
  <tr>
    <td>UNMATCHED_AV_DISCONTINUITY_FOUND</td>
    <td>92</td>
    <td>Unmatched Audio and Video 不連続が見つかりました。</td>
  </tr>
  <tr>
    <td>TRICKPLAY_ENDED_DUE_TO_ERROR</td>
    <td>93</td>
    <td>トリック再生モードでメディアを再生中にエラーが発生しました。 トリック再生モードが終了し、ストリームが一時停止します。 Play() を呼び出して、メディアを通常モードで再生します。</td>
  </tr>
  <tr>
    <td>LIVE_WINDOW_MOVED_AHEAD</td>
    <td>95</td>
    <td>プレーヤーはライブウィンドウから出ているので、追いつくには早送りする必要があります。</td>
  </tr>
</table>

---
description: MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。
title: MediaResource 情報にアクセスするための MediaPlayerItem メソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# MediaResource 情報にアクセスするための MediaPlayerItem メソッド {#mediaplayeritem-methods-for-accessing-mediaresource-information}

MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。

| メソッド | 説明 |
|--- |--- |
| **広告タグ** |  |
| リスト`<String>` getAdTags() | 広告配置プロセスに使用される広告タグのリストを提供します。 |
| **ライブストリーム** |  |
| boolean isLive(); | ストリームがライブの場合は true、VOD の場合は false です。 |
| **DRM 保護** |  |
| boolean isProtected(); | ストリームが DRM 保護されている場合は true です。 |
| リスト`<DRMMetadataInfo>` getDRMMetadataInfos(); | マニフェストで検出されたすべての DRM メタデータオブジェクトのリストを表示します。 |
| **クローズドキャプション** |  |
| boolean hasClosedCaptions(); | クローズドキャプショントラックが使用可能な場合は true。 |
| リスト`<ClosedCaptionsTrack>` getClosedCationsTracks(); | 使用可能なクローズドキャプショントラックのリストを提供します。 |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | SelectClosedCaptionsTrack で選択された、現在のクローズドキャプショントラックを取得します。 |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack ) | クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 |
| **代替オーディオトラック** |  |
| boolean hasAlternateAudio(); | ストリームに代替オーディオトラックがある場合は true。 注意：メイン（デフォルト）のオーディオトラックも、代替オーディオトラックリストの一部です。  Android 向け TVSDK は、メインのオーディオトラックを、代替オーディオトラックリストの項目の 1 つと見なします。 このため、 MediaPlayerItem.hasAlternateAudio が false を返す唯一のケースは、ストリームにオーディオがまったくない場合です。 コンテンツにオーディオトラックが 1 つだけある場合、このメソッドは true を返し、  `MediaPlayerItem.getAudioTracks`  は、単一の要素（デフォルトのオーディオトラック）を持つリストを返します。 |
| リスト`<AudioTrack>` getAudioTracks(); | 使用可能な代替オーディオトラックのリストを提供します。 |
| AudioTrack getSelectedAudioTrack(); | selectAudioTrack で選択されたオーディオトラックを取得します。 |
| selectAudioTrack ( AudioTrack audioTrack ) | 現在のオーディオトラックにするオーディオトラックを選択します。 |
| **時間指定メタデータ** |  |
| boolean hasTimedMetadata(); | ストリームに時間指定メタデータが関連付けられている場合は true。 |
| リスト`<TimedMetadata>` getTimedMetadata(); | ストリームに関連付けられている時間指定メタデータオブジェクトのリストを提供します。 |
| **複数のプロファイル（ビットレート）** |
| boolean isDynamic(); | ストリームがマルチビットレート (MBR) ストリームの場合は true。 |
| リスト`<Profile>` getProfiles(); | 関連するビットレートプロファイルのリストを提供します。 各プロファイルについて、ビットレート、プロファイルの高さおよび幅を取得できます。 |
| プロファイル getSelectedProfile() | 現在選択されているプロファイルを取得します。 |
| **トリック再生** |  |
| boolean isTrickPlaySupported(); | True を指定すると、プレーヤーが早送り、巻き戻しおよび再開をサポートします。 |
| リスト`< Float>` getAvailablePlaybackRates() | トリック再生機能のコンテキストで使用可能な再生率のリストを提供します。 |
| Float getSelectedPlaybackRate() | 現在選択されている再生速度を取得します。 |
| MediaPlayerItemConfig getConfig() | この項目に関連付けられている MediaPlayerItemConfig インスタンスを返します。 |
| **メディアリソース** |  |
| MediaResource getResource(); | この項目に関連付けられているメディアリソースを返します。 |
| int getResourceId() | この項目に関連付けられているメディア識別子を返します。 この ID は、アイテムが MediaPlayerItemLoader.load を使用して読み込まれる際に設定されます。 |

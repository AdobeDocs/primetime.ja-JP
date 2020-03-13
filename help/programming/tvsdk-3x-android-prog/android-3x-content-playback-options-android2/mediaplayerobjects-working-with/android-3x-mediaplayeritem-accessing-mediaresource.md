---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-title: MediaResource情報にアクセスするためのMediaPlayerItemメソッド
title: MediaResource情報にアクセスするためのMediaPlayerItemメソッド
uuid: 46845583-0a76-4411-a8bc-0a16ebfe8e6e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# MediaResource情報にアクセスするためのMediaPlayerItemメソッド {#mediaplayeritem-methods-for-accessing-mediaresource-information}

MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。

| メソッド | 説明 |
|--- |--- |
| **広告タグ** |  |
| List`<String>` getAdTags() | 広告配置プロセスに使用される広告タグのリストを提供します。 |
| **ライブストリーム** |  |
| boolean isLive(); | ストリームがライブの場合はtrue、VODの場合はfalse。 |
| **DRM保護** |  |
| boolean isProtected(); | ストリームがDRM保護されている場合はtrue。 |
| List`<DRMMetadataInfo>` getDRMMetadataInfos(); | マニフェスト内で見つかったすべてのDRMメタデータオブジェクトを一覧表示します。 |
| **クローズドキャプション** |  |
| boolean hasClosedCaptions(); | クローズドキャプショントラックが使用可能な場合はtrue。 |
| List`<ClosedCaptionsTrack>` getClosedCationsTracks(); | 使用可能なクローズドキャプショントラックのリストを提供します。 |
| ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); | SelectClosedCaptionsTrackで選択された現在のクローズドキャプショントラックを取得します。 |
| selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) | クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 |
| **代替オーディオトラック** |  |
| boolean hasAlternateAudio(); | ストリームに代替オーディオトラックが含まれる場合はtrue。 注意： メイン（デフォルト）のオーディオトラックも代替オーディオトラックリストの一部です。  Android向けTVSDKは、メインのオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、MediaPlayerItem.hasAlternateAudioがfalseを返すのは、ストリームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つしかない場合、このメソッドはtrueを返し、1つの `MediaPlayerItem.getAudioTracks` 要素（デフォルトのオーディオトラック）を持つリストを返します。 |
| List`<AudioTrack>` getAudioTracks(); | 使用可能な代替オーディオトラックのリストを表示します。 |
| AudioTrack getSelectedAudioTrack(); | selectAudioTrackで選択されたオーディオトラックを取得します。 |
| selectAudioTrack ( AudioTrack audioTrack ) | 現在のオーディオトラックにするオーディオトラックを選択します。 |
| **時間指定メタデータ** |  |
| boolean hasTimedMetadata(); | ストリームに時間指定メタデータが関連付けられている場合はtrue。 |
| List`<TimedMetadata>` getTimedMetadata(); | ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 |
| **複数のプロファイル（ビットレート）** |
| boolean isDynamic(); | ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 |
| List`<Profile>` getProfiles(); | 関連するビットレートプロファイルのリストを表示します。 各プロファイルのビットレートと高さと幅を取得できます。 |
| Profile getSelectedProfile() | 現在選択されているプロファイルを取得します。 |
| **トリック再生** |  |
| boolean isTrickPlaySupported(); | プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrueです。 |
| List`< Float>` getAvailablePlaybackRates() | トリック再生機能のコンテキストで使用可能な再生速度のリストを表示します。 |
| Float getSelectedPlaybackRate() | 現在選択されている再生レートを取得します。 |
| MediaPlayerItemConfig getConfig() | この項目に関連付けられたMediaPlayerItemConfigインスタンスを返します。 |
| **メディアリソース** |  |
| MediaResource getResource(); | この項目に関連付けられたメディアリソースを返します。 |
| int getResourceId() | この項目に関連付けられたメディア識別子を返します。 このIDは、アイテムがMediaPlayerItemLoader.loadを使用して読み込まれるときに設定されます。 |
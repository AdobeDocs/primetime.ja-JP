---
description: 代替オーディオ（遅延バインディング）を使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ユーザはビデオの再生時に言語トラックを選択できます。
seo-description: 代替オーディオ（遅延バインディング）を使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ユーザはビデオの再生時に言語トラックを選択できます。
seo-title: 代替オーディオ
title: 代替オーディオ
uuid: d7e61a2a-1985-4dba-9c6d-0e139ffde46a
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 代替オーディオ{#alternate-audio}

代替オーディオ（遅延バインディング）を使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ユーザはビデオの再生時に言語トラックを選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDKは、現在のビデオのイ `MediaPlayerItem` ンスタンスを作成すると、使用可能な各オーディオト `AudioTrack` ラックのアイテムを作成します。 項目にはプロパティ `name` が含まれています。この文字列には、通常、そのトラックの言語に関するユーザーが認識できる説明が含まれています。 項目には、そのトラックをデフォルトで使用するかどうかに関する情報も含まれます。

ビデオの再生時に、使用可能なオーディオトラックのリストを確認し、必要に応じてユーザがオーディオトラックを選択し、選択したトラックで再生するビデオを設定できます。

まれですが、作成後に追加のオーディオトラックが使用可能になった場合、TVSDKは `MediaPlayerItem`イベントを発生さ `MediaPlayerItem.AUDIO_UPDATED` せます。

## APIの追加 {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

代替オーディオをサポートするために、次のAPIが追加されました。

`hasAlternateAudio`

指定したメディアにデフォルト以外の代替オーディオトラックが含まれている場合、このboolean関数はを返しま `true`す。 代替オーディオトラックがない場合は、を返します `false`。

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

指定したメディアで現在使用可能なすべてのオーディオトラックのリストを返します。

```
virtual PSDKErrorCode getAudioTracks(PSDKImmutableArray<AudioTrack>*& out) const { 
    if (_audioTracks) { 
        out = _audioTracks; 
        out->addRef(); 
        return kECSuccess; 
    } 
    return kECDataNotAvailable; 
} 
```

`getSelectedAudioTrack`

現在選択されている代替オーディオトラックおよび言語などのプロパティを返す関数です。 トラックの自動選択も抽出できます。

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const { 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

`selectAudioTrack`

この関数は、再生する代替オーディオトラックを選択します。

```
PSDKErrorCode MediaPlayerItemImpl::selectAudioTrack(const AudioTrack &audioTrack) { 
    _lastPlayedAudioTrack = _currentAudioTrack; 
    if(_mediaPlayer && _mediaPlayer->_trickPlay) 
        return kECUnsupportedOperation; 
    _currentAudioTrack = audioTrack; 
    PSDKErrorCode result = kECSuccess; 
    if (_currentAudioTrack) { 
        media::TimeLine* timeline = NULL; 
        if (_mediaPlayer->_fragHttpStreamer) 
            _mediaPlayer->_fragHttpStreamer->GetTimeLine(&timeline); 
        if (timeline) { 
            for (int32_t i = timeline->GetFirstPeriodIndex(); i <= timeline->GetLastPeriodIndex(); i++){ 
                media::ErrorCode error = selectTrack(timeline,_mediaPlayer->_fragHttpStreamer, i, audioTrack.getName(), media::kSTTAudioIndex); 
                return _mediaPlayer->convertToPSDKError(error); 
            } 
        } 
    }   
    return result; 
}
```


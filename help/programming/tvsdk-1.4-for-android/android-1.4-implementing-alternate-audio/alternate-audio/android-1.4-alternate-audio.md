---
description: 代替のオーディオ（遅延バインディング）を使用すると、ビデオトラックに使用可能なオーディオトラック間で切り替えることができます。 これにより、ユーザーはビデオの再生時に言語トラックを選択できます。
title: 代替オーディオ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# 代替オーディオ {#alternate-audio}

代替のオーディオ（遅延バインディング）を使用すると、ビデオトラックに使用可能なオーディオトラック間で切り替えることができます。 これにより、ユーザーはビデオの再生時に言語トラックを選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDK が `MediaPlayerItem` 現在のビデオのインスタンスに対して、 `AudioTrack` 各オーディオトラックの項目。 項目には、 `name` プロパティ。通常、ユーザーが認識できるトラックの言語の説明を含む文字列です。 項目には、デフォルトでそのトラックを使用するかどうかに関する情報も含まれています。

ビデオを再生する時に、使用可能なオーディオトラックのリストを求めることができます。必要に応じて、ユーザーに選択してもらい、選択したトラックで再生するビデオを設定できます。

まれですが、 `MediaPlayerItem`を指定した場合、 TVSDK は `MediaPlayerItem.AUDIO_UPDATED` イベント。

## 追加された API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

代替オーディオをサポートするために、次の API が追加されました。

`hasAlternateAudio`

指定したメディアに、デフォルトのトラック以外の代替オーディオトラックがある場合、このブール関数は `true`. 代替オーディオトラックがない場合は、 `false`.

```
bool MediaPlayerItemImpl::hasAlternateAudio() const { 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

この関数は、指定したメディア内の、現在使用可能なすべてのオーディオトラックのリストを返します。

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

現在選択されている代替オーディオトラックおよび言語などのプロパティを返すこの関数。 トラックの自動選択も抽出できます。

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

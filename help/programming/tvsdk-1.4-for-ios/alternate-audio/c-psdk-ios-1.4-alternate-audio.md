---
description: 代替（遅延バインディング）オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ビデオをいつ再生するかをユーザーが選択できます。
title: 代替オーディオ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# 概要{#alternate-audio-overview}

代替（遅延バインディング）オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ビデオをいつ再生するかをユーザーが選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDKは、現在のビデオの`MediaPlayerItem`インスタンスを作成すると、使用可能な各オーディオトラックに対して`AudioTrack`アイテムを作成します。 項目には`name`プロパティが含まれています。通常、このプロパティには、そのトラックの言語に関するユーザーが認識できる説明が含まれています。 項目には、そのトラックをデフォルトで使用するかどうかに関する情報も含まれます。

ビデオの再生時に、使用可能なオーディオトラックのリストを尋ねることができます。必要に応じて、ユーザがオーディオトラックを選択し、選択したトラックで再生するビデオを設定できます。

まれにですが、`MediaPlayerItem`の作成後に追加のオーディオトラックが使用可能になった場合、TVSDKは`MediaPlayerItem.AUDIO_UPDATED`イベントを実行します。

## API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}を追加

代替オーディオをサポートするために、次のAPIが追加されました。

`hasAlternateAudio`

指定したメディアにデフォルト以外の代替オーディオトラックがある場合、このboolean関数は`true`を返します。 代替オーディオトラックがない場合は、`false`を返します。

```
bool MediaPlayerItemImpl::hasAlternateAudio() const 
{ 
    return _hasAlternateAudio; 
}
```

** `getAudioTracks`**

この関数は、指定されたメディア内の現在使用可能なすべてのオーディオトラックのリストを返します。

```
virtual PSDKErrorCode getAudioTracks(PSDKImmutableArray<AudioTrack>*& out) const 
    { 
        if (_audioTracks) 
        { 
            out = _audioTracks; 
            out->addRef(); 
            return kECSuccess; 
        } 
        return kECDataNotAvailable; 
    }
```

`getSelectedAudioTrack`

現在選択されている代替オーディオトラックおよび言語などのプロパティを返す関数。 トラックの自動選択も抽出できます。

```
PSDKErrorCode MediaPlayerItemImpl::getSelectedAudioTrack(AudioTrack &out) const 
{ 
    out = _currentAudioTrack; 
    return kECSuccess; 
}
```

`selectAudioTrack`

この関数は、再生する代替オーディオトラックを選択します。

```
PSDKErrorCode MediaPlayerItemImpl::selectAudioTrack(const AudioTrack &audioTrack) 
{ 
    _lastPlayedAudioTrack = _currentAudioTrack; 
    if(_mediaPlayer && _mediaPlayer->_trickPlay) 
        return kECUnsupportedOperation; 
    _currentAudioTrack = audioTrack; 
    PSDKErrorCode result = kECSuccess; 
    if (_currentAudioTrack) 
    { 
        media::TimeLine* timeline = NULL; 
        if (_mediaPlayer->_fragHttpStreamer) 
            _mediaPlayer->_fragHttpStreamer->GetTimeLine(&timeline); 
        if (timeline) 
        { 
            for (int32_t i = timeline->GetFirstPeriodIndex(); i <= timeline->GetLastPeriodIndex(); i++){ 
                media::ErrorCode error = selectTrack(timeline,_mediaPlayer->_fragHttpStreamer, i, audioTrack.getName(), media::kSTTAudioIndex); 
                return _mediaPlayer->convertToPSDKError(error); 
            } 
        } 
    }   
    return result; 
}
```


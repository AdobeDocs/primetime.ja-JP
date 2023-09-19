---
description: 代替オーディオを使用すると、ビデオトラックの使用可能なオーディオトラック間を切り替えることができます。 ユーザーは、ビデオの再生時に、優先言語トラックを選択できます。
title: 代替オーディオ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 概要 {#alternate-audio-overview}

代替オーディオを使用すると、ビデオトラックの使用可能なオーディオトラック間を切り替えることができます。 ユーザーは、ビデオの再生時に、優先言語トラックを選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDK が `MediaPlayerItem` 現在のビデオのインスタンスに対して、 `AudioTrack` 各オーディオトラックの項目。 項目には、 `name` プロパティ。通常、ユーザーが認識できる、そのトラックの言語の説明を含む文字列です。 項目には、デフォルトでそのトラックを使用するかどうかに関する情報も含まれています。 ビデオを再生する時に、使用可能なオーディオトラックのリストを求めることができます。オプションで、ユーザーがトラックを選択できるようにし、選択したトラックで再生するようにビデオを設定できます。

>[!TIP]
>
>まれですが、 TVSDK が `MediaPlayerItem`を指定した場合、 TVSDK は `MediaPlayerItem.AUDIO_TRACK_UPDATED` イベント。

## 追加された API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

代替オーディオをサポートするために、次の API が追加されました。

**`hasAlternateAudio`**

指定したメディアに、デフォルトのトラック以外の代替オーディオトラックがある場合、このブール関数は `true`. 代替オーディオトラックがない場合は、 `false`.

```java
boolean hasAlternateAudio();
```

**`getAudioTracks`**

この関数は、指定したメディア内の、現在使用可能なすべてのオーディオトラックのリストを返します。

```java
List<AudioTrack> getAudioTracks();
```

**`getSelectedAudioTrack`**

現在選択されている代替オーディオトラックおよび言語などのプロパティを返すこの関数。 トラックの自動選択も抽出できます。

```java
AudioTrack getSelectedAudioTrack();
```

**`selectAudioTrack`**

この関数は、再生する代替オーディオトラックを選択します。

```java
void selectAudioTrack(AudioTrack audioTrack);
```

例：

```java
private void onPrepared() { 
    // Select the AA track in PREPARED State 
    boolean hasAlternateAudio = _mediaPlayer.getCurrentItem().hasAlternateAudio(); 
    if(hasAlternateAudio) { 
        AudioTrack selectedAudioTrack =  
          _mediaPlayer.getCurrentItem().getSelectedAudioTrack(); 
 
        if (selectedAudioTrack == null) {  
            // Selecting default audio track  
            // If index is 1 it will select alternate audio track  
            selectedAudioTrack = _mediaPlayer.getCurrentItem().getAudioTracks().get(0);  
        } 
    } 
    _mediaPlayer.getCurrentItem().selectAudioTrack(selectedAudioTrack); 
} 
```

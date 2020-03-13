---
description: 代替オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 ユーザは、ビデオの再生時に好みの言語トラックを選択できます。
seo-description: 代替オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 ユーザは、ビデオの再生時に好みの言語トラックを選択できます。
seo-title: 代替オーディオ
title: 代替オーディオ
uuid: 86aa5393-6a9e-49db-807b-7299e6b4ab2b
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# 概要 {#alternate-audio-overview}

代替オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 ユーザは、ビデオの再生時に好みの言語トラックを選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDKは、現在のビデオのイ `MediaPlayerItem` ンスタンスを作成すると、使用可能な各オーディオト `AudioTrack` ラックのアイテムを作成します。 項目にはプロパティ `name` が含まれます。これは、通常、そのトラックの言語に関するユーザーが認識できる説明を含む文字列です。 項目には、そのトラックをデフォルトで使用するかどうかに関する情報も含まれます。 ビデオの再生時に、使用可能なオーディオトラックのリストを確認し、必要に応じてユーザがトラックを選択できるようにし、選択したトラックでビデオを再生するように設定できます。

>[!TIP]
>
>まれに、TVSDKがオーディオトラックを作成した後に追加のオーディオトラックが使用可能になった場合、TVSDK `MediaPlayerItem`はイベントを実行 `MediaPlayerItem.AUDIO_TRACK_UPDATED` します。

## APIの追加 {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}

代替オーディオをサポートするために、次のAPIが追加されました。

`hasAlternateAudio`

指定したメディアにデフォルト以外の代替オーディオトラックが含まれている場合、このboolean関数はを返しま `true`す。 代替オーディオトラックがない場合は、を返します `false`。

```java
boolean hasAlternateAudio();
```

** `getAudioTracks`**

指定したメディアで現在使用可能なすべてのオーディオトラックのリストを返します。

```java
List<AudioTrack> getAudioTracks();
```

`getSelectedAudioTrack`

現在選択されている代替オーディオトラックおよび言語などのプロパティを返す関数です。 トラックの自動選択も抽出できます。

```java
AudioTrack getSelectedAudioTrack();
```

`selectAudioTrack`

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


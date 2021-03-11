---
description: 代替オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 ユーザーは、ビデオを再生するときに好みの言語トラックを選択できます。
title: 代替オーディオ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# 概要{#alternate-audio-overview}

代替オーディオを使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 ユーザーは、ビデオを再生するときに好みの言語トラックを選択できます。

<!--<a id="section_E4F9DC28A2944BD08B4190A7F98A8365"></a>-->

TVSDKは、現在のビデオの`MediaPlayerItem`インスタンスを作成すると、使用可能な各オーディオトラックに対して`AudioTrack`アイテムを作成します。 項目には`name`プロパティが含まれています。これは通常、ユーザーが認識できるそのトラックの言語の説明を含む文字列です。 項目には、そのトラックをデフォルトで使用するかどうかに関する情報も含まれます。 ビデオの再生時に、使用可能なオーディオトラックのリストを求めることができます。必要に応じて、トラックの選択を許可し、選択したトラックでビデオを再生するように設定できます。

>[!TIP]
>
>まれにですが、TVSDKが`MediaPlayerItem`を作成した後に追加のオーディオトラックが使用可能になった場合、TVSDKは`MediaPlayerItem.AUDIO_TRACK_UPDATED`イベントを実行します。

## API {#section_87C42C30BA8C4F58A2DAB7CE07FCD3DE}を追加

代替オーディオをサポートするために、次のAPIが追加されました。

`hasAlternateAudio`

指定したメディアにデフォルト以外の代替オーディオトラックがある場合、このboolean関数は`true`を返します。 代替オーディオトラックがない場合は、`false`を返します。

```java
boolean hasAlternateAudio();
```

** `getAudioTracks`**

この関数は、指定されたメディア内の現在使用可能なすべてのオーディオトラックのリストを返します。

```java
List<AudioTrack> getAudioTracks();
```

`getSelectedAudioTrack`

現在選択されている代替オーディオトラックおよび言語などのプロパティを返す関数。 トラックの自動選択も抽出できます。

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


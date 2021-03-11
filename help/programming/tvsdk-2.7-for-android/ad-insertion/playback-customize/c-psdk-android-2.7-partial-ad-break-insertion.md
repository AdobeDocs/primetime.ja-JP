---
title: 広告の時間の部分挿入
description: 広告の時間の部分挿入
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# 部分的な広告ブレークの挿入{#partial-ad-break-insertion}

テレビのようなエクスペリエンスで、広告の途中やライブストリームに参加できるようにすることができます。 部分的な広告の時間機能を使用すると、クライアントがミッドロール内のライブストリームを開始した場合に、そのミッドロール内で開始する、テレビのようなエクスペリエンスを模倣できます。 テレビチャネルに切り替えるのと同じで、CMはシームレスに走ります。

例えば、ユーザーが90秒の広告の時間（3つの30秒の広告）の途中で加入し、10秒で2番目の広告に入った場合（つまり、広告の時間が始まる40秒の時点）、次のようになります。

* 2番目の広告は、残りの時間（20秒）に再生され、次に3番目の広告が再生されます。
* 部分的に再生された広告（2番目の広告）の広告トラッカーは起動されません。 3番目の広告のトラッカーのみが起動されます。

この動作は、デフォルトでは有効になっていません。 アプリでこの機能を有効にするには、次の手順を実行します。

1. AdvertisingMetadataクラスのメソッドsetEnableLivePrerollを使用して、ライブプリロールを無効にします。

   ```
   advertisingMetadata.setLivePreroll(false)  
   advertisingMetadata.setPreroll(false)
   ```

1. 部分的な広告ブレークの挿入の環境設定をオンにします。 この機能をオンにするには、MediaPlayerインターフェイスの新しいメソッドsetPartialAdBreakPrefを使用します。 この基本設定の現在の状態を調べるには、getPartialAdBreakPrefメソッドを使用します。

   ```
   MediaPlayer mediaPlayer = new MediaPlayer(getActivity().getApplicationContext()); 
    mediaPlayer.setPartialAdBreakPref(true);
   ```


---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---


# デフォルトの再生動作の使用 {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のタスクのいずれかを実行します。

   * 独自の `AdvertisingFactory` クラスを実装する場合は、に対してnullを返し `createAdPolicySelector`ます。

   * クラスのカスタム実装がない場合、TVSDKはデフォルトの広告ポリシーセレクターを使用し `AdvertisingFactory` ます。

## カスタマイズされた再生の設定 {#set-up-customized-playback}

広告動作は、カスタマイズまたは上書きできます。

広告動作をカスタマイズまたは上書きする前に、に広告ポリシーインスタンスを登録します。
広告動作をカスタマイズするには、次のいずれかを実行します。

* インターフェイスとそのすべてのメソッドを実装し `AdPolicySelector` ます。

   デフォルトの広告動作をす **べて上書きする必要がある場合は** 、このオプションをお勧めします。

* クラスを拡張し、カスタマイズが必要な動作に対してのみ実装を提供し `DefaultAdPolicySelector` ます。

   一部のデフォルトの動作のみを上書きする必要がある場合は **** 、このオプションをお勧めします。

広告動作をカスタマイズするには：

1. インターフェイスとそのすべてのメソッドを実装し `AdPolicySelector` ます。
1. TVSDKが使用するポリシーインスタンスを、広告ファクトリを介して割り当てます。

   >[!NOTE]
   >
   >class CustomContentFactory extends ContentFactory &amp;lbrace;
   >...
   >@Override
   >public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) &amp;lbrace;
   >return new CustomAdPolicySelector(mediaPlayerItem);
   >&amp;rbrace;
   >...
   >&amp;rbrace;
   >// register custom content factory with media player
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >//この設定は、読み込み中に後で渡されます>リソース
   >mediaPlayer.replaceCurrentResource(resource, config);

1. カスタマイズを実装します。

---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作の使用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# デフォルトの再生動作{#use-the-default-playback-behavior}を使用

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のタスクのいずれかを実行します。

   * 独自の`AdvertisingFactory`クラスを実装する場合、`createAdPolicySelector`に対してnullを返します。

   * `AdvertisingFactory`クラスのカスタム実装がない場合、TVSDKはデフォルトの広告ポリシーセレクターを使用します。

## カスタマイズ再生の設定{#set-up-customized-playback}

広告動作は、カスタマイズまたは上書きできます。

広告動作をカスタマイズまたは上書きする前に、に広告ポリシーインスタンスを登録します。
広告動作をカスタマイズするには、次のいずれかを実行します。

* `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。

   デフォルトの広告動作&#x200B;**すべての**&#x200B;を上書きする必要がある場合は、このオプションをお勧めします。

* `DefaultAdPolicySelector`クラスを拡張し、カスタマイズが必要な動作のみに実装を提供します。

   デフォルトの動作の&#x200B;**一部**&#x200B;のみを上書きする必要がある場合は、このオプションをお勧めします。

広告動作をカスタマイズするには：

1. `AdPolicySelector`インターフェイスとそのすべてのメソッドを実装します。
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

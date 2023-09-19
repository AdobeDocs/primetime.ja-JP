---
description: デフォルトの広告動作を使用するように選択できます。
title: デフォルトの再生動作を使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# デフォルトの再生動作を使用 {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のいずれかのタスクを実行します。

   * 独自の `AdvertisingFactory` クラスは、の null を返します。 `createAdPolicySelector`.

   * のカスタム実装がない場合、 `AdvertisingFactory` クラスの場合、 TVSDK はデフォルトの広告ポリシーセレクターを使用します。

## カスタマイズされた再生の設定 {#set-up-customized-playback}

広告の動作をカスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをに登録します。
広告の動作をカスタマイズするには、次のいずれかの操作を行います。

* の実装 `AdPolicySelector` インターフェイスおよびそのすべてのメソッド。

  このオプションは、 **すべて** デフォルトの広告の動作です。

* の拡張 `DefaultAdPolicySelector` クラスを作成し、カスタマイズが必要な動作に対してのみ実装を提供します。

  このオプションは、 **some** のデフォルトの動作を設定します。

広告の動作をカスタマイズするには：

1. の実装 `AdPolicySelector` インターフェイスとそのすべてのメソッド。
1. 広告ファクトリを通じて、TVSDK が使用するポリシーインスタンスを割り当てます。

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
   >//カスタムコンテンツファクトリをメディアプレーヤーに登録します。
   >MediaPlayerItemConfig config = new MediaPlayerItemConfig();
   >config.setAdvertisingFactory(new CustomContentFactory());
   >//この設定は、後で読み込み中に渡される > リソース
   >mediaPlayer.replaceCurrentResource(resource, config);

1. カスタマイズ機能を実装します。

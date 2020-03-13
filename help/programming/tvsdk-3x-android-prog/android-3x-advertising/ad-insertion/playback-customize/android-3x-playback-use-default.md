---
description: デフォルトの広告動作を使用するように選択できます。
seo-description: デフォルトの広告動作を使用するように選択できます。
seo-title: デフォルトの再生動作の使用
title: デフォルトの再生動作の使用
uuid: 36f76c42-4c6c-4620-9b47-ec97519a642a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# デフォルトの再生動作の使用 {#use-the-default-playback-behavior}

デフォルトの広告動作を使用するように選択できます。

1. デフォルトの動作を使用するには、次のいずれかのタスクを実行します。

   * 独自のクラスを実装する `AdvertisingFactory` 場合は、に対してnullを返しま `createAdPolicySelector`す。

   * クラスのカスタム実装がない場合、TVSDKはデフォ `AdvertisingFactory` ルトの広告ポリシーセレクターを使用します。

## カスタマイズされた再生の設定 {#set-up-customized-playback}

広告の動作は、カスタマイズまたは上書きできます。

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをに登録します。
動作をカスタマイズするには、次のいずれかの操作を行います。

* インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。

   すべてのデフォルトの広告動作を上書きする必要がある場合 **は** 、このオプションをお勧めします。

* クラスを拡張 `DefaultAdPolicySelector` し、カスタマイズが必要な動作のみを実装します。

   このオプションは、一部のデフォルトの動作のみを上書きする **必要が** ある場合に推奨されます。

動作をカスタマイズするには：

1. インターフェイス `AdPolicySelector` とそのすべてのメソッドを実装します。
1. TVSDKが広告ファクトリを介して使用するポリシーインスタンスを割り当てます。

>[!NOTE]
>class CustomContentFactory extends ContentFactory {
>...
>@上書き
>public AdPolicySelector retrieveAdPolicySelector>>(MediaPlayerItem mediaPlayerItem) {
>return new CustomAdPolicySelector(mediaPlayerItem);
>}
>...
>}
>//カスタムコンテンツファクトリをメディアプレイヤーに登録
>MediaPlayerItemConfig config = new MediaPlayerItemConfig();
>config.setAdvertisingFactory(new CustomContentFactory());
>//この設定は、読み込み中に後で渡される>リソース
>mediaPlayer.replaceCurrentResource(resource, config);

1. カスタマイズを実装します。
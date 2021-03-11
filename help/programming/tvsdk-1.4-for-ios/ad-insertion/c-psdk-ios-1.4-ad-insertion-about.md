---
description: 広告挿入は、広告をビデオオンデマンド(VOD)、ライブストリーミング、および広告トラッキングと広告再生を含むリニアストリーミング用に解決します。 TVSDKは、広告サーバーに必要なリクエストを行い、指定されたコンテンツの広告に関する情報を受信し、コンテンツ内の広告を各フェーズで配置します。
title: 広告の挿入
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---


# 広告を挿入{#insert-ads}

広告挿入は、広告をビデオオンデマンド(VOD)、ライブストリーミング、および広告トラッキングと広告再生を含むリニアストリーミング用に解決します。 TVSDKは、広告サーバーに必要なリクエストを行い、指定されたコンテンツの広告に関する情報を受信し、コンテンツ内の広告を各フェーズで配置します。

*`ad break`*&#x200B;には、1つ以上の広告が順に再生されます。 TVSDKは、1つ以上の広告の時間のメンバーとして、メインコンテンツに広告を挿入します。

>[!TIP]
>
>広告にエラーがある場合、TVSDKはその広告を無視します。

## VOD広告を解決して挿入{#section_157344F857C64F36B48AD441F6E7FABA}

TVSDKは、VOD広告の解決と挿入の使用例をいくつかサポートしています。

* プリロール広告の挿入。広告はコンテンツの先頭に挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも1つの広告が挿入されます。
* ポストロール広告の挿入。コンテンツの末尾に少なくとも1つの広告が追加されます。

TVSDKは、広告を解決し、広告サーバーが定義する場所に広告を挿入し、バーチャルタイムラインを計算してから再生開始を実行します。 再生開始後は、広告が挿入されたり、広告が削除されたりするなどの変更は発生しません。

## ライブおよびリニア広告を解決して挿入{#section_A6A1BB262D084462A1D134083556B7CC}

TVSDKは、ライブおよびリニア広告の解決と挿入の使用例をいくつかサポートしています。

* プリロール広告の挿入。コンテンツの先頭に少なくとも1つの広告が挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも1つの広告が挿入されます。

TVSDKは、広告を解決し、ライブストリームまたはリニアストリーム内でキューポイントを検出すると広告を挿入します。 デフォルトでは、TVSDKは、広告の解決および配置時に、有効な広告マーカーとして次のキューをサポートします。

* # EXT-X-CUEPOINT
* # EXT-X-AD
* # EXT-X-CUE
* # EXT-X-CUE-OUT

これらのマーカーは、メタデータフィールドの秒単位の`DURATION`とキューの一意のIDを必要とします。 例：

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

追加のキューについて詳しくは、[カスタムタグの登録](../ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-custom-tags-subscribe.md)を参照してください。

## クライアント広告{#section_12355C7A35F14C15A2A18AAC90FEC2F5}を追跡

TVSDKは、VODおよびライブ/リニアストリーミング用の広告を自動的に追跡します。

通知は、広告の開始時と終了時に関する情報など、広告の進行状況をアプリに知らせるために使用します。

## 早期広告ブレークリターンの実装{#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。

以下に、早い広告の時間が返される例を示します。

* 特定のスポーツイベントでの広告の時間の長さ。

   デフォルトの継続時間が指定されていますが、ゲームが終了する前に再開された場合は、広告の時間を終了する必要があります。
* ライブストリーム内の広告の時間中の緊急信号。

広告の時間を早く終了する機能は、スプライスインタグまたはキューインタグと呼ばれるマニフェスト内のカスタムタグで識別されます。 TVSDKを使用すると、アプリケーションはこれらのスプライスインタグをサブスクライブして、スプライスインオポチュニティを提供できます。

* `#EXT-X-CUE-IN`タグをスプライスインオポチュニティとして使用し、早期広告ブレークの返り値を実装するには：

   1. タグをサブスクライブします。

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. キュ追加ーインオポチュニティリゾルバー。

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* スプライスアウトとスプライスインで同じタグを共有するには：

   1. アプリケーションが同じキューを共有して、キューアウト/スプライスアウトとキューイン/スプライスインを示している場合は、`PTDefaultAdOpportunityResolver`を拡張して`preparePlacementOpportunity`メソッドを実装します。

      >[!TIP]
      >
      >次のコードは、アプリに`isCueInOpportunity`メソッドの実装があることを前提としています。
      >
      >
      ```
      >- (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
      >{ 
      >       if ([self isCueInOpportunity:timedMetadata]) 
      >       { 
      >               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
      >       } 
      >       else 
      >       { 
      >               return [super preparePlacementOpportunity:timedMetadata]; 
      >       } 
      >}
      >```

   1. `PTDefaultMediaPlayerClientFactory`インスタンスに拡張オポチュニティリゾルバーを登録します。

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Clear existing resolver and register the new opportunity resolver 
      [clientFactory clearOpportunityResolvers]; 
      [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
      ```


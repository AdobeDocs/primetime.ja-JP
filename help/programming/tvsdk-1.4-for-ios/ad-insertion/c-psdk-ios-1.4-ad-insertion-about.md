---
description: 広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。
seo-description: 広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。
seo-title: 広告の挿入
title: 広告の挿入
uuid: 6fffb340-65ea-4c47-a55b-c0ec4917d37c
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告の挿入{#insert-ads}

広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。

「」には、 *`ad break`* 順番に再生される1つ以上の広告が含まれます。 TVSDKは、1つ以上の広告の時間のメンバーとして、メインコンテンツに広告を挿入します。

>[!TIP]
>
>広告にエラーがある場合、TVSDKはその広告を無視します。

## VOD広告の解決と挿入 {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDKは、VOD広告の解決と挿入に関するいくつかの使用例をサポートしています。

* プリロール広告の挿入。広告がコンテンツの先頭に挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも1つの広告が挿入されます。
* ポストロール広告の挿入。コンテンツの末尾に少なくとも1つの広告が追加されます。

TVSDKは、広告を解決し、広告サーバーで定義された場所に広告を挿入し、再生が開始される前に仮想タイムラインを計算します。 再生開始後は、広告の挿入や削除などの変更は行われません。

## ライブおよびリニア広告の解決と挿入 {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDKは、ライブおよびリニア広告の解決と挿入に関するいくつかの使用例をサポートしています。

* プリロール広告の挿入。コンテンツの先頭に少なくとも1つの広告が挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも1つの広告が挿入されます。

TVSDKは、広告を解決し、ライブストリームまたはリニアストリームでキューポイントが見つかった場合に広告を挿入します。 デフォルトでは、TVSDKは、広告の解決および配置時に、有効な広告マーカーとして次のキューをサポートします。

* # EXT-X-CUEPOINT
* # EXT-X-AD
* # EXT-X-CUE
* # EXT-X-CUE-OUT

これらのマーカーは、メタデータフィールドの秒 `DURATION` 数とキューの一意のIDを必要とします。 例：

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

追加のキューについて詳しくは、「カスタムタグの [登録」を参照してください](../ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-custom-tags-subscribe.md)。

## クライアント広告の追跡 {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDKは、VODおよびライブ/リニアストリーミング用の広告を自動的に追跡します。

通知は、広告の開始日時や終了日時など、広告の進行状況をアプリに知らせるために使用します。

## 早期の広告ブレークリターンの実装 {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。

以下に、早期広告の時間のリターンの例を示します。

* 特定のスポーツイベントでの広告の時間の長さ。

   デフォルトの期間が指定されていますが、ゲームが終了する前に再開した場合は、広告の時間を終了する必要があります。
* ライブストリームの広告の時間中の緊急信号。

広告の時間を早く終了する機能は、スプライスインまたはキューインタグと呼ばれるマニフェスト内のカスタムタグを通じて識別されます。 TVSDKを使用すると、アプリケーションはこれらのスプライスインタグをサブスクライブして、スプライスインオポチュニティを提供できます。

* タグをスプライス `#EXT-X-CUE-IN` インオポチュニティとして使用し、早期の広告ブレークの返却を実装するには：

   1. タグを購読します。

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. キューインオポチュニティリゾルバーを追加します。

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* スプライスアウトとスプライスインで同じタグを共有するには：

   1. キューアウト/スプライスアウトとキューイン/スプライスインを示す同じキューをアプリケーションが共有している場合は、メソッドを拡張し `PTDefaultAdOpportunityResolver` て実装してく `preparePlacementOpportunity` ださい。

      >[!TIP]
      >
      >次のコードは、アプリにこのメソッドの実装があることを前提とし `isCueInOpportunity` ています。
      >
      >
      >
      >
      >
      ```>
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
      >```       >
      >



   1. インスタンスで拡張オポチュニティリゾルバーを登録 `PTDefaultMediaPlayerClientFactory` します。

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Clear existing resolver and register the new opportunity resolver 
      [clientFactory clearOpportunityResolvers]; 
      [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
      ```


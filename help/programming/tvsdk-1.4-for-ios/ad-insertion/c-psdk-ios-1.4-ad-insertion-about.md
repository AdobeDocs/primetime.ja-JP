---
description: 広告挿入は、広告をビデオオンデマンド (VOD)、ライブストリーミング、広告トラッキングと広告再生を伴うリニアストリーミング用に解決します。 TVSDK は、広告サーバーに対して必要なリクエストを実行し、指定されたコンテンツの広告に関する情報を受け取り、コンテンツ内に広告をフェーズで配置します。
title: 広告の挿入
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---

# 広告の挿入{#insert-ads}

広告挿入は、広告をビデオオンデマンド (VOD)、ライブストリーミング、広告トラッキングと広告再生を伴うリニアストリーミング用に解決します。 TVSDK は、広告サーバーに対して必要なリクエストを実行し、指定されたコンテンツの広告に関する情報を受け取り、コンテンツ内に広告をフェーズで配置します。

An *`ad break`* には、1 つ以上の広告が順に再生されます。 TVSDK は、1 つ以上の広告の時間のメンバーとして、メインコンテンツに広告を挿入します。

>[!TIP]
>
>広告にエラーがある場合、 TVSDK は広告を無視します。

## VOD 広告の解決と挿入 {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK は、VOD 広告の解決と挿入の使用例を複数サポートしています。

* プリロール広告の挿入。広告はコンテンツの先頭に挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも 1 つの広告が挿入されます。
* ポストロール広告の挿入。コンテンツの末尾に 1 つ以上の広告が追加されます。

TVSDK は、広告を解決し、広告サーバーが定義した場所に広告を挿入し、再生が開始される前に仮想タイムラインを計算します。 再生の開始後、挿入された広告や挿入された広告が削除されるなどの変更は発生しない可能性があります。

## ライブおよびリニア広告の解決と挿入 {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK は、ライブおよびリニア広告の解決と挿入の使用例を複数サポートしています。

* プリロール広告の挿入。コンテンツの先頭に少なくとも 1 つの広告が挿入されます。
* ミッドロール広告の挿入。コンテンツの途中に少なくとも 1 つの広告が挿入されます。

TVSDK は、ライブストリームまたはリニアストリームでキューポイントを検出すると、広告を解決し、広告を挿入します。 デフォルトでは、 TVSDK は、広告の解決および配置時に、次のキューを有効な広告マーカーとしてサポートします。

* #EXT-X-CUEPOINT
* #EXT-X-AD
* #EXT-X-CUE
* #EXT-X-CUE-OUT

これらのマーカーは、メタデータフィールドの `DURATION` 秒単位で表示され、キューの一意の ID。 例：

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

追加のキューについて詳しくは、 [カスタムタグを購読](../ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-custom-tags-subscribe.md).

## クライアント広告の追跡 {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK は、VOD およびライブ/リニアストリーミングの広告を自動的に追跡します。

通知は、広告の開始日時や終了日時など、広告の進行状況をアプリケーションに通知するために使用します。

## 早期広告ブレークリターンの実装 {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

ライブストリーム広告の挿入の場合、ブレーク内のすべての広告が最後まで再生される前に、広告ブレークから終了する必要が生じる場合があります。

早期広告ブレークの戻り値の例を次に示します。

* 特定のスポーツイベントでの広告ブレークの期間。

  デフォルトのデュレーションを指定していますが、ブレークが終了する前にゲームが再開された場合、広告ブレークを終了する必要があります。
* ライブストリームの広告ブレーク中の緊急シグナル。

広告ブレークを早期に終了する機能は、スプライスインまたはキューインタグと呼ばれるマニフェスト内のカスタムタグによって識別されます。 TVSDK を使用すると、アプリケーションはこれらのスプライスインタグをサブスクライブして、スプライスインの機会を提供できます。

* 次の手順で `#EXT-X-CUE-IN` スプライスインオポチュニティとしてタグ付けし、早期広告ブレークリターンを実装します。

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

   1. アプリケーションが同じキューを共有して、キューアウト/スプライスアウトとキューイン/スプライスインを示している場合は、を拡張します。 `PTDefaultAdOpportunityResolver` およびを実装します。 `preparePlacementOpportunity` メソッド。

      >[!TIP]
      >
      >次のコードは、アプリに `isCueInOpportunity` メソッド。
      >
      >```
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
      >

   1. 拡張オポチュニティリゾルバーを `PTDefaultMediaPlayerClientFactory` インスタンス。

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Clear existing resolver and register the new opportunity resolver 
      [clientFactory clearOpportunityResolvers]; 
      [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
      ```

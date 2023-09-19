---
description: MediaPlayerItemConfig クラスを使用して、ストリーム内のカスタムタグ名を設定できます。
title: タグの Config クラスメソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# タグの Config クラスメソッド{#config-class-methods-for-tags}

MediaPlayerItemConfig クラスを使用して、ストリーム内のカスタムタグ名を設定できます。

新しい `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

以下に、 `MediaPlayerItemConfig` カスタムタグの管理には、次のメソッドを使用します。

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグを購読する</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>サブスクライブ済みタグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 </p> <p>アプリケーションは、を介して送信されるすべてのタグに対しても自動的にサブスクライブされます <span class="codeph"> adTags </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ </b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;adTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.adTags; 
    </code> </td> 
   <td colname="col2"> <p>広告タグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;adTags&nbsp;=&nbsp;["#EXT-X-CUE"];mediaPlayerItemConfig.adTags&nbsp;=&nbsp;adTags;
    </code> </td> 
   <td colname="col2"> <p>デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の点に注意してください。

* カスタムタグ名には、 `#` プレフィックス。

  例： `#EXT-X-ASSET` は正しいカスタムタグ名ですが、 `EXT-X-ASSET` が正しくありません。

* メディアストリームの読み込み後は、設定を変更できません。

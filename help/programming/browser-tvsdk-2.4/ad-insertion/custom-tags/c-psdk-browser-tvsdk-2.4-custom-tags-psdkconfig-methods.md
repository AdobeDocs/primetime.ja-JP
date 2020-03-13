---
description: MediaPlayerItemConfigクラスを使用して、ストリーム内のカスタムタグ名を設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、ストリーム内のカスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 222a0349-58d5-4bf3-9d03-e5920610faf5
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# タグのConfigクラスメソッド{#config-class-methods-for-tags}

MediaPlayerItemConfigクラスを使用して、ストリーム内のカスタムタグ名を設定できます。

To create a new `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

メソッドを使用してカスタムタグを管理 `MediaPlayerItemConfig` する方法について、次に示す情報を示します。

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>サブスクライブされたタグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 </p> <p>また、アプリケーションは、adTagsを通じて送信されるすべてのタグを自動的にサブスクライブ <span class="codeph"> していま </span>す。 </p> </td> 
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

* カスタムタグ名に接頭辞を含める必要が `#` あります。

   例えば、は正し `#EXT-X-ASSET` いカスタムタグ名ですが、正しくあ `EXT-X-ASSET` りません。

* メディアストリームの読み込み後は、設定を変更できません。


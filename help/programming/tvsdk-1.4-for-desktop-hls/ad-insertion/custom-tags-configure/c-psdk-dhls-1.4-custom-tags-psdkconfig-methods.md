---
description: MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。
seo-description: MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 3317fc8b-c13c-4e7d-8334-aa8cdf40fa05
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# タグのConfigクラスメソッド{#config-class-methods-for-tags}

MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定しないメディアストリームに対して、グローバル設定を自動的に適用します。

とは、次の `PSDKConfig` 両方の `MediaPlayerItemConfig` メソッドを使用して、カスタムタグを管理します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get subscribeTags():Vector.&lt;文字列&gt;</span> </td> 
   <td colname="col2"> サブスクライブされたタグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set subscribeTags():Vector.&lt;文字列&gt;</span> </td> 
   <td colname="col2">アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 <p>また、アプリケーションは、adTagsを通じて送信されるすべてのタグを自動的にサブスクライブ <span class="codeph"> します</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get adTags():Vector.&lt;文字列&gt;</span> </td> 
   <td colname="col2"> 広告タグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set adTags():Vector.&lt;文字列&gt;</span> </td> 
   <td colname="col2"> デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 </td> 
  </tr> 
 </tbody> 
</table>

次の点に注意してください。

* setterメソッドでは、tagsパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKはIDをスローしま `IllegalArgumentException`す。
* カスタムタグ名には、#プレフィックスを含める必要があります。

   例えば、は正し `#EXT-X-ASSET` いカスタムタグ名ですが、正しくあ `EXT-X-ASSET` りません。
* メディアストリームの読み込み後は、設定を変更できません。


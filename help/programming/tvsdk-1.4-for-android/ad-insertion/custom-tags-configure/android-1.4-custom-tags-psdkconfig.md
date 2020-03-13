---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: f2758085-8e49-4eaf-82bb-4a2e4dd8accb
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# タグのConfigクラスメソッド{#config-class-methods-for-tags}

MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定しないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` 次のメソッドを使用して、カスタムタグを管理します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags() </span> </td> 
   <td colname="col2"> サブスクライブされたタグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 <p>また、アプリケーションは、setAdTagsを通じて送信されるすべてのタグを自動的にサブスクラ <span class="codeph"> イブしま </span>す。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags(); </span> </td> 
   <td colname="col2"> 広告タグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags); </span> </td> 
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


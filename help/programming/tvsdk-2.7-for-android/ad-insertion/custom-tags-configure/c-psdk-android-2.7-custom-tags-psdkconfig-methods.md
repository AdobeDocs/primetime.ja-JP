---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 64284876-1f31-47e0-a99b-3bfe17e10707
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# タグのConfigクラスメソッド {#config-class-methods-for-tags}

MediaPlayerItemConfigクラスを使用して、TVSDK内のカスタムタグ名をグローバルに設定できます。

TVSDKは、ストリーム固有の設定を指定しないメディアストリームに、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` 次のメソッドを使用して、カスタムタグを管理します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags </span> </td> 
   <td colname="col2"> <p>サブスクライブされたタグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 </p> <p>また、アプリケーションは、setAdTagsを通じて送信されるすべてのタグを自動的にサブスクラ <span class="codeph"> イブしま </span>す。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags; </span> </td> 
   <td colname="col2"> <p>広告タグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の点に注意してください。

* setterメソッドでは、tagsパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKはIDをスローしま `IllegalArgumentException`す。
* カスタムタグ名に接頭辞を含める必要が `#` あります。

   例えば、は正し `#EXT-X-ASSET` いカスタムタグ名ですが、正しくあ `EXT-X-ASSET` りません。

* メディアストリームの読み込み後は、設定を変更できません。

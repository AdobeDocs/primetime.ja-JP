---
description: MediaPlayerItemConfig クラスを使用して、 TVSDK 内でグローバルにカスタムタグ名を設定できます。
title: タグの Config クラスメソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# タグの Config クラスメソッド{#config-class-methods-for-tags}

MediaPlayerItemConfig クラスを使用して、 TVSDK 内でグローバルにカスタムタグ名を設定できます。

TVSDK は、ストリーム固有の設定を指定しないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` は、カスタムタグを管理する次のメソッドを公開しています。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグを購読する</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags() </span> </td> 
   <td colname="col2"> サブスクライブ済みタグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 <p>また、アプリケーションは、 <span class="codeph"> setAdTags </span>. </p> </td> 
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

* setter メソッドでは、タグパラメーターに null 値を含めることはできません。

  検出された場合、 TVSDK は `IllegalArgumentException`.
* カスタムタグ名には#プレフィックスを含める必要があります。

  例： `#EXT-X-ASSET` は正しいカスタムタグ名ですが、 `EXT-X-ASSET` が正しくありません。
* メディアストリームの読み込み後は、設定を変更できません。

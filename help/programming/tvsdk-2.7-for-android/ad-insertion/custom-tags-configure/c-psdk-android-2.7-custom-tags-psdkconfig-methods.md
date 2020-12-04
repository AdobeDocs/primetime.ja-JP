---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 64284876-1f31-47e0-a99b-3bfe17e10707
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# タグ{#config-class-methods-for-tags}のConfigクラスメソッド

MediaPlayerItemConfigクラスを使用して、TVSDK内でカスタムタグ名をグローバルに設定できます。

TVSDKは、ストリーム固有の設定を指定していないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` カスタムタグを管理するには、次のメソッドを公開します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags  </span> </td> 
   <td colname="col2"> <p>サブスクライブされたタグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags);  </span> </td> 
   <td colname="col2"> <p>アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 </p> <p>また、アプリケーションは、<span class="codeph"> setAdTags </span>を通じて送信されるすべてのタグも自動的にサブスクライブされます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags;  </span> </td> 
   <td colname="col2"> <p>広告タグの現在のリストを取得します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags);  </span> </td> 
   <td colname="col2"> <p>デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

次の点に注意してください。

* setterメソッドでは、タグパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKは`IllegalArgumentException`をスローします。
* カスタムタグ名には、`#`プレフィックスを含める必要があります。

   例えば、`#EXT-X-ASSET`は正しいカスタムタグ名ですが、`EXT-X-ASSET`は正しくありません。

* メディアストリームの読み込み後は、設定を変更できません。

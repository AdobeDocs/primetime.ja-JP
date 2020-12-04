---
description: MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-description: MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: f2758085-8e49-4eaf-82bb-4a2e4dd8accb
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# tags{#config-class-methods-for-tags}のConfigクラスメソッド

MediaPlayerItemConfigクラスを使用して、TVSDK内でグローバルにカスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定していないメディアストリームに対して、グローバル設定を自動的に適用します。

`MediaPlayerItemConfig` カスタムタグを管理するには、次のメソッドを公開します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getSubscribedTags()  </span> </td> 
   <td colname="col2"> サブスクライブされたタグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags);  </span> </td> 
   <td colname="col2"> アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 <p>また、アプリケーションは、<span class="codeph"> setAdTags </span>を通じて送信されるすべてのタグも自動的にサブスクライブされます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags();  </span> </td> 
   <td colname="col2"> 広告タグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags);  </span> </td> 
   <td colname="col2"> デフォルトのオポチュニティジェネレーターが使用する広告タグのリストを設定します。 </td> 
  </tr> 
 </tbody> 
</table>

次の点に注意してください。

* setterメソッドでは、タグパラメーターにnull値を含めることはできません。

   検出された場合、TVSDKは`IllegalArgumentException`をスローします。
* カスタムタグ名にはプレフィックス#を含める必要があります。

   例えば、`#EXT-X-ASSET`は正しいカスタムタグ名ですが、`EXT-X-ASSET`は正しくありません。
* メディアストリームの読み込み後は、設定を変更できません。


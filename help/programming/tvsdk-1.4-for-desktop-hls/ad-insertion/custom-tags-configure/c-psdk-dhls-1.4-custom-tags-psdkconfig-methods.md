---
description: MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。
seo-description: MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。
seo-title: タグのConfigクラスメソッド
title: タグのConfigクラスメソッド
uuid: 3317fc8b-c13c-4e7d-8334-aa8cdf40fa05
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# tags{#config-class-methods-for-tags}のConfigクラスメソッド

MediaPlayerItemConfigクラスを使用してTVSDK内でグローバルに、またはMediaPlayerItemConfigクラスを使用してストリームベースに、カスタムタグ名を設定できます。

TVSDKは、ストリーム固有の設定を指定していないメディアストリームに対して、グローバル設定を自動的に適用します。

`PSDKConfig`と`MediaPlayerItemConfig`の両方が、カスタムタグを管理するために次のメソッドを公開します。

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>特定のカスタムタグのサブスクライブ</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get subscribeTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> サブスクライブされたタグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set subscribeTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2">アプリケーションに公開されるサブスクライブ済みタグのリストを設定します。 <p>また、アプリケーションは、<span class="codeph"> adTags</span>を通じて送信されるすべてのタグも自動的にサブスクライブします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>デフォルトのオポチュニティディテクターで使用される広告タグのカスタマイズ  </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function get adTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> 広告タグの現在のリストを取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public function set adTags():Vector.&lt;string&gt;</span> </td> 
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


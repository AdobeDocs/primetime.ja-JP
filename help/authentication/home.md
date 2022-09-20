---
title: ようこそAdobe&reg；へようこそPrimetime 認証
description: ようこそAdobe&reg；へようこそPrimetime 認証の概要
source-git-commit: 79cdd0b7ae33d7c1d2bec970ecd3654aea4fdab0
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 1%

---


# Adobe® Primetime 認証へようこそ {#overview}

Adobe Primetime認証は、TV Everywhere の使用権限付与ソリューションで、リソースへのアクセスを要求するユーザーがそのリソースに対する使用権限を付与されているかどうかを判断するためのモジュラーフレームワークを提供します。 Primetime 認証エンタイトルメントソリューションに参加するために、コンテンツプロバイダー（プログラマー）および有料テレビプロバイダー (MVPD) は、エンタイトルメントシステムと Primetime 認証ワークフローを統合します。 このドキュメントサイトでは、統合プロセスの詳細と既存のパートナー向けのヒントを提供します。

フィードバックは常に感謝されています。

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## よく読まれるヘルプと FAQ {#help-and-faqs-resources}

|注目すべきトピック| |-| |<ul>&lt;>iOSプロモーション一時パスのホームベース認証 (HBA) HBA Infographic Primetime TVE ダッシュボードユーザーガイド|

| プログラマー向け | MVPD の場合 |
|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| <ul><li>プログラマー向けキックスタートガイド</li><li> MVPD セレクター (「picker」)</li><li>ユーザーメタデータ</li></ul> | <ul><li>MVPD キックスタートガイド</li><li>認証</li><li>認証</li><li>ログアウト</li></ul> |
| **ネイティブアプリクライアント向け** | **全員に対して** |
| <ul><li>iOS Technical Overview</li><li>Android 技術概要</li></ul> | <ul><li>テクニカルペーパー</li><li>エスカレーション手順</li><li>サポートされるシステム</li><li>用語集</li><li>テクニカルノート</li></ul> |
| スマートデバイスの場合 |  |
| <ul><li>クライアントレスの技術概要</li><li>クライアントレス API</li></ul> |

<div id="startcontainer">

<div class="table">

<table id="start-topic-table" data-border="0" data-cellpadding="0" data-cellspacing="0" style="height: 380px; width: 584px;">
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">よくあるヘルプと FAQ</th>
<th style="text-align: left;"> </th>
<th style="text-align: left;"> </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><strong>プログラマー向け</strong></p>
<p> </p>
<ul>
<li><a href="#">プログラマー向けキックスタートガイド</a></li>
</ul>
<ul>
<li><a href="#obtaining_mvpd_list">MVPD セレクター (「picker」)</a></li>
<li><a href="#">ユーザーメタデータ</a></li>
</ul>
 
<p><strong>ネイティブアプリクライアント向け</strong></p>
<ul>
<li><a href="#">iOS Technical Overview</a></li>
<li><a href="#">Android 技術概要</a></li>
</ul>
<p> </p>
<p><strong>スマートデバイスの場合</strong></p>
<ul>
<li><a href="http://tve.helpdocsonline.com/rest-api-overview">クライアントレスの技術概要</a></li>
<li><a href="https://tve.helpdocsonline.com/rest-api-reference">クライアントレス API</a></li>
</ul>
<p> </p></td>
<td style="text-align: left;"><p><strong>MVPD の場合</strong></p>
<p> </p>
<ul>
<li><a href="#">MVPD キックスタートガイド</a></li>
<li><a href="#">認証</a></li>
<li><a href="#">認証</a></li>
</ul>
<ul>
<li><a href="#">ログアウト</a></li>
</ul>
 
<p><strong>全員に対して</strong></p>
<ul>
<li><a href="#">テクニカルペーパー</a></li>
<li><a href="#">エスカレーション手順</a></li>
<li><a href="#">サポートされるシステム</a></li>
<li><a href="#">用語集</a></li>
<li><a href="#">テクニカルノート</a></li>
</ul></td>
<td style="text-align: left;"><p><strong>注目すべきトピック <img src="https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/1468939180_new.png?dc=201607190941-4" /></strong></p>
<p> </p>
<ul>
<li><a href="http://tve.helpdocsonline.com/ios/tvos-sso-changes">iOSのシングルサインオン</a></li>
<li><a href="#">プロモーション一時パス</a></li>
<li><a href="#">HBA（ホーム・ベース認証）</a></li>
<li><a href="https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/files/AdobeNewsletterHBA.pdf">HBA の解説図</a></li>
<li><a href="#">Primetime TVE ダッシュボードユーザーガイド</a></li>
</ul></td>
</tr>
</tbody>
</table>

</div>

<div class="block">

## 答えが見つからない場合

[**お問い合わせ**](mailto:tve-support@adobe.com)

[サポートチームにメールを送信する](mailto:tve-support@adobe.com) は、問題またはインシデントレポートの最初の手順でもあります。

次の場合、 [**<span style="color:#ff0000;">重大度 1 有効</span>**](http://tve.helpdocsonline.com/escalation-procedures-2)
問題が発生し、メールで 30 分が経過しました\
応答がない場合、\
[エスカレーション手順](#) 文書\
電話番号を呼び出すために使用します。

<div>

 

</div>

</div>

</div>

 

<span style="font-family: verdana, geneva, sans-serif;">必要な情報を見つけるには：</span>

<span style="font-family: verdana, geneva, sans-serif;">** **   **検索** Primetime 認証ヘルプデスク上の任意の場所で、このドキュメントを含む結果を確認できます。\
     **参照** 左側のナビゲーションパネルのフォルダー階層を使用して、すべての Primetime 認証ドキュメントを参照してください。\
     **フィルター** フォルダー階層を表示するには、ナビゲーションウィンドウ上部の「 」フィールドに用語を入力します。\
     **ブックマーク** Web ブラウザーを使用して、関心のあるページへの「ディープリンク」。</span>

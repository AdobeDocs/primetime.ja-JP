---
title: /authenticate リクエストでの「&'reg_code」の使用の回避
description: /authenticate リクエストでの「&'reg_code」の使用の回避
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# /authenticate リクエストでの「&amp;&#39;reg_code」の使用の回避 {#clientless-avoid-using-reg_code-in-authenticate-request}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

</br>



## 問題

IE 9 ブラウザは「\®」を特別なコマンドとして解釈し、®に変換します。 

## 説明

この `/authenticate` リクエストは次のように構成されます。

 

```
    <FQDN>authenticate? requestor_id=someRequestor&reg_code=EKAFMFI&domain_name=someRequestor.com&noflash=true&mso_id=someMvpd&redirect_url=someRequestor.redirect.url.html
```
 

...IE ブラウザーによって以下のように解釈され、この形式でAdobeに送信されます。

 

```
    <FQDN>authenticate?requestor_id=someRequestor&reg;_code=EKAFMFI&domain_name=someRequestor.com&noflash=true&mso_id=someMvpd&redirect_url=someRequestor.redirect.url.html
```
 

requestor\_id は univision®\_code=EKAFMFI と解釈されます。これは、&#39;&amp;&#39;がないため、Adobeは `regCode` パラメーターを使用してトークンを関連付けます。  AuthN トークンがまったく作成されない場合があります。その場合、 `/checkauthn` の呼び出しは、トークンを見つけることができません。



## 解決策

この問題は、次のいずれかのオプションで解決する必要があります。

1. を使用しない `&reg_code` 他のクエリー文字列パラメーター間のパラメーター。  代わりに、リクエスト URL の最初のクエリー文字列パラメーターに移動し、次のようにリクエスト URL を作成します。\
    

       &lt;fqdn>authenticate?reg_code =EKAFMFI&amp;requestor_id=someRequestor&amp;domain_name=someRequestor.com&amp;noflash=true&amp;mso_id=someMvpd&amp;redirect_url=someRequestor.redirect.url.html
   

   この方法で、 `&reg` param が正しく解釈されない問題を修正しました。

1. 標準化 `&reg_code` 使用中 `&amp;reg_code`.

1. Adobeでは、AuthN トークンの作成に失敗した場合、認証呼び出しに応じてエラーコードを 2 番目の画面に送り返す新しい機能が導入される可能性がありました。


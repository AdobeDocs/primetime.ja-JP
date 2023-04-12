---
title: サービスプロバイダー範囲
description: サービスプロバイダー範囲
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# サービスプロバイダー範囲 {#service-provoider-scoping}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## 概要 {#overview}

MVPD とのAdobe Primetime認証統合のデフォルトの実装は、 **OLCA 仕様**. OLCA 仕様（6.5、サブジェクト識別子）の認証要件の節では、サブジェクト識別子のサービスプロバイダ (SP) の範囲を示すことが可能であると述べています。 （件名識別子は、MVPD が SP に返す不明化されたユーザー ID です）。  Adobe Primetime認証統合では、MVPDs が SP 認証要求のスコーピングを有効にする必要があります。

Adobe Primetime認証がプログラマの SP の役割を引き継ぐ場合は、認証要求の SP スコープを有効にするカスタマイズを実装する必要があります。  これは、MVPD が SAML アサーションで MVPD の ID プロバイダー (IdP) に渡されるネットワークブランドを識別できるようにするために行う必要があります。  スコーピングは、次の節で説明する 2 つの方法のいずれかで実装できます。

## サービスプロバイダー範囲 {#service-provider-scoping}

Adobe Primetime認証では、次の 2 つの方法で認証要求の SP スコープを有効にできます。

* **SAML 発行者アプローチ。**  このアプローチでは、「リクエスト元 ID」が SAML 認証リクエストの SAML 発行者文字列に追加されます。

* **カスタムスコーピングプロパティのアプローチです。**  このアプローチでは、「Requestor ID」が SAML 認証リクエストのカスタム「Scoping」プロパティとして明示的に含まれます。

>[!NOTE]
>
>「リクエスト元 ID」は、Adobe Primetime認証がプログラマーのネットワークブランド ( 例：「CNN」はターナーネットワークのブランドの 1 つです )。

### SAML 発行者アプローチ {#saml-issuer-approach}

このアプローチでは SAML を使用します `<Issuer>` 要素を含める必要があります。

```xml
...
<saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">
    http://saml.sp.adobe.adobe.com/on-behalf-of/requestorID
</saml:Issuer>
...
```

### カスタムスコーププロパティのアプローチ {#custom-scoping-property-approach}

この方法では、SAML 認証要求の次のスニペットに示すように、「Scoping」という名前のカスタムプロパティを使用します。

```xml
...
<samlp:Scoping xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">
    <samlp:RequesterID xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol">requestorID</samlp:RequesterID>
</samlp:Scoping>
...
```

<!--
>[!RELATEDINFORMATION]
>* [MVPD Authentication](/help/authentication/authn-usecase.md)
>* **OLCA Specification**
-->
---
title: Adobe Primetime認証（オプション）
description: Adobe Primetime認証（オプション）
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Adobe Primetime認証（オプション） {#adobe-primetime-authentication-optional}

コンテンツのパッケージ化に使用されるDRMポリシーが匿名ポリシーの場合、すべてのライセンス要求にライセンスが発行されます。 オプションで、Primetime Cloud DRMは、Adobe Primetime認証を介した認証もサポートします。 この機能を有効にした場合、クライアントデバイスが最初にPrimetime認証トークンを取得し、カスタム認証トークンを設定する適切なクライアントAPI(`setAuthenticationToken`)を介してローカルに設定しない限り、ライセンスは発行されません。 Primetime認証を認証ワークフローに統合する方法について詳しくは、次を参照してください。[Adobe Primetime認証。](https://tve.helpdocsonline.com/home)

ライセンスの取得中に、DRMポリシーでPri metime認証が必要と記載されている場合、ライセンスサーバーはPrimetime認証の短いメディアトークンを解析および検証します。 DRMポリシーで`ResourceID`または`RequestorID`を指定した場合は、ライセンスサーバーもこれらのプロパティに対してトークンを検証します。 設定されていない場合、ライセンスサーバーは、トークンの検証時にプロパティを「null」に指定します。 トークンの検証に成功した場合にのみ、ライセンスが発行されます。それ以外の場合は、305のサブエラーコード（ユーザーが認証されていません）を含む3328 DRMErrorEventがクライアントからディスパッチされます。

Primetime認証パラメーターは、Primetime認証を必要とするコンテンツのパッケージ化に使用されるポリシーで指定する必要があります。

関連するプロパティは次のとおりです。

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Primetime認証を(DRM)ライセンスローテーション機能と組み合わせて使用する場合、Primetime認証の短いメディアトークン(SMT)の有効期限が短いことに注意してください。 アプリケーションでライセンスローテーション（例：*ブラックアウト*&#x200B;の使用例をサポートするため）を使用する場合、アプリケーションは、ライセンスを回転する前に、この点に注意し、Primetime認証のShort Media Tokenを更新する必要があります。
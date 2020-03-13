---
seo-title: Adobe Primetime認証（オプション）
title: Adobe Primetime認証（オプション）
uuid: fa6225d6-e0e5-4fcc-ac26-4ff54f9f334a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime認証（オプション） {#adobe-primetime-authentication-optional}

コンテンツのパッケージ化に使用されるDRMポリシーが匿名ポリシーの場合、すべてのライセンス要求に対してライセンスが発行されます。 オプションで、Primetime Cloud DRMは、Adobe Primetime認証を介した認証もサポートします。 この機能を有効にした場合、クライアントデバイスが最初にPrimetime認証トークンを取得し、カスタム認証トークンを設定する適切なクライアントAPI( `setAuthenticationToken`)を介してローカルに設定しない限り、ライセンスは発行されません。 Primetime認証を認証ワークフローに統合する方法について詳しくは、次を参照してください。 [Adobe Primetime認証。](https://tve.helpdocsonline.com/home)

ライセンスの取得中に、DRMポリシーがPri metime認証が必要と述べている場合、ライセンスサーバーはPrimetime認証の短いメディアトークンを解析して検証します。 DRMポリシーでORが指定されている場合、ラ `ResourceID` イセンスサ `RequestorID`ーバーは、これらのプロパティに対するトークンも検証します。 設定されていない場合、ライセンスサーバーはトークンの検証中にプロパティを「null」として指定します。 トークンの検証が成功した場合にのみ、ライセンスが発行されます。それ以外の場合は、305のサブエラーコード（ユーザーが認証されていません）を含む3328 DRMErrorEventがクライアントからディスパッチされます。

Primetime認証パラメーターは、Primetime認証を必要とするコンテンツのパッケージ化に使用されるポリシーで指定する必要があります。

関連するプロパティは次のとおりです。

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>(DRM)ライセンスローテーション機能と組み合わせてPrimetime認証を使用する場合、Primetime認証の短いメディアトークン(SMT)の有効期限が短いことに注意してください。 アプリケーションでライセンスローテーション(例： *Blackouts* （ブラックアウト）の使用を計画している場合)は、ライセンスを回転させる前に、アプリケーションがこのことを認識し、Primetime認証のShort Media Tokenを更新する必要があります。
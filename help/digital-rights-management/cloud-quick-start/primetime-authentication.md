---
title: Adobe Primetime認証（オプション）
description: Adobe Primetime認証（オプション）
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Adobe Primetime認証（オプション） {#adobe-primetime-authentication-optional}

コンテンツのパッケージ化に使用される DRM ポリシーが匿名ポリシーの場合、すべてのライセンス要求に対してライセンスが発行されます。 オプションで、Primetime Cloud DRM はAdobe Primetime認証を介した認証もサポートします。 この機能が有効になっている場合、クライアントデバイスが最初に Primetime 認証トークンを取得し、適切なクライアント API( `setAuthenticationToken`) を使用して、カスタム認証トークンを設定します。 Primetime 認証を認証ワークフローに統合する方法について詳しくは、次を参照してください。 [Adobe Primetime認証。](https://tve.helpdocsonline.com/home)

ライセンスの取得中に、DRM ポリシーに Pri metime 認証が必要と記載されている場合、ライセンスサーバーは Primetime 認証のショートメディアトークンを解析および検証します。 DRM ポリシーで `ResourceID` または `RequestorID`を指定した場合、ライセンスサーバーはこれらのプロパティに対してトークンを検証します。 設定されていない場合、ライセンスサーバはトークンの検証中にプロパティを「null」として指定します。 トークンの検証が成功した場合にのみ、ライセンスが発行されます。それ以外の場合は、305 サブエラーコード (User Not Authorized) を含む 3328 DRMErrorEvent がクライアントによってディスパッチされます。

Primetime 認証が必要となる設定のコンテンツのパッケージ化に使用するポリシーで、Primetime 認証パラメーターを指定する必要があります。

関連するプロパティは次のとおりです。

```
#policy.customProp.1=adobePass.required=<TRUE or FALSE> 
#policy.customProp.1=adobePass.requestorID=<Requestor ID String> 
#policy.customProp.1=adobePass.resourceID=<Resource ID String>
```

>[!NOTE]
>
>Primetime 認証を (DRM) ライセンスのローテーション機能と組み合わせて使用する場合、Primetime 認証のショートメディアトークン (SMT) の有効期限が短くなることにご注意ください。 アプリケーションがライセンスローテーションを利用する予定の場合 ( 例： *ブラックアウト* 使用例を参照 )、アプリケーションはこの点を認識し、ライセンスを回転する前に Primetime 認証のショートメディアトークンを更新する必要があります。

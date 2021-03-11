---
title: DRMポリシーの操作の概要
description: DRMポリシーの操作の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# 概要{#working-with-drm-policies-overview}

コンテンツプロバイダーは、Primetime DRM SDKを使用してメディアファイルにDRMポリシーを適用できます。 管理者は、その後、ポリシー管理APIを使用してDRMポリシーを作成、表示詳細を作成、更新できます。

*`DRM policy`*&#x200B;は、セキュリティ設定、認証要件、使用権限などの情報の集まりです。 ポリシーでは、ユーザーがコンテンツを表示する方法を定義します。 DRMポリシー、暗号化、および署名により、コンテンツの提供元は、コンテンツがどの程度広く配布されても、コンテンツの制御を維持できます。

DRMポリシーは、ライセンスを生成する際にライセンスサーバーで使用されるテンプレートとして機能します。 クライアントは、ライセンスを要求する前にDRMポリシーを参照し、クライアントがサーバーにライセンス要求を発行する前にユーザーに認証を求める必要があるかどうかを判断することもできます。

保護されたコンテンツは、AdobeFlash Media ServerまたはHTTPサーバーを使用して配信できます。 ユーザーは、Primetime DRM SDKを使用して構築されたカスタムプレーヤーで、保護されたコンテンツをダウンロードして再生できます。

DRMポリシーは、クライアントに付与される1つ以上の権限を指定します。 通常、DRMポリシーには最低でも&#x200B;*`Play Right`*&#x200B;が含まれます。 また、複数の再生権限を指定することもできます。それぞれに異なる制限があります。 クライアントが複数の再生権限を持つライセンスを受け取ると、すべての制限を満たす最初のライセンスが使用されます。 例えば、異なるプラットフォームで異なる出力保護設定を適用できます。

この例を示すサンプルコードについては、「リファレンス実装のコマンドラインツール[!DNL samples]」ディレクトリの`CreatePolicyWithOutputProtection.java`を参照してください。

Primetime DRMポリシー管理APIを使用して、以下のタスクを完了できます。

* ポリシーの作成と更新
* 表示DRMポリシーの詳細
* DRMポリシーの更新リストの管理

Java APIについて詳しくは、*Primetime DRM API Reference*&#x200B;を参照してください。

Primetime DRM Policy Managerについて詳しくは、『Primetime DRM Reference Implementationsの使用&#x200B;*』ガイドを参照してください。*

---
seo-title: DRMポリシーの操作の概要
title: DRMポリシーの操作の概要
uuid: 32423448-013c-4183-bea8-e14b6690abdb
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# 概要 {#working-with-drm-policies-overview}

コンテンツプロバイダーは、Primetime DRM SDKを使用してメディアファイルにDRMポリシーを適用できます。 管理者は、ポリシー管理APIを使用して、DRMポリシーの作成、詳細の表示および更新を行うことができます。

Aは、セ *`DRM policy`* キュリティ設定、認証要件、使用権限などの情報の集まりです。 ポリシーは、ユーザーがコンテンツを表示する方法を定義します。 DRMポリシー、暗号化、署名を使用すると、コンテンツの提供者は、コンテンツがどの程度広く配布されても、コンテンツの制御を維持できます。

DRMポリシーは、ライセンスを生成する際にライセンスサーバーが使用するテンプレートとして機能します。 クライアントは、ライセンスを要求する前にDRMポリシーを参照し、クライアントがサーバーにライセンス要求を発行する前にユーザーに認証を求める必要があるかどうかを判断することもできます。

保護されたコンテンツは、Adobe Flash Media ServerまたはHTTPサーバーを使用して配信できます。 ユーザーは、Primetime DRM SDKを使用して構築されたカスタムプレーヤーで、保護されたコンテンツをダウンロードして再生できます。

DRMポリシーは、クライアントに付与される1つ以上の権限を指定します。 通常、DRMポリシーには、少なくともが含まれま *`Play Right`*&#x200B;す。 また、複数の再生権限を指定し、それぞれ異なる制限を設けることもできます。 クライアントが複数の再生権限を持つライセンスを受け取ると、すべての制限を満たす最初のライセンスが使用されます。 例えば、異なるプラットフォームで異なる出力保護設定を適用することができます。

この例を `CreatePolicyWithOutputProtection.java` 示すサンプルコードについては、Reference Implementation Command Line Tools [!DNL samples] ディレクトリのを参照してください。

Primetime DRMポリシー管理APIを使用して、次のタスクを実行できます。

* ポリシーの作成と更新
* DRMポリシーの詳細の表示
* DRMポリシーの更新リストの管理

Java APIについて詳し *くは、『Primetime DRM API* Reference』を参照してください。

Primetime DRM Policy Managerにつ *いて詳しくは、『Primetime DRM Referenceの実装の使用* 』ガイドを参照してください。

---
seo-title: カスタムDRMポリシーの作成（オプション）
title: カスタムDRMポリシーの作成（オプション）
uuid: 701b51d9-6dde-4c21-bc5b-09e612582968
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# カスタムDRMポリシーの作成（オプション）{#create-custom-drm-policies-optional}

Primetime Cloud DRM保護キットには、パッケージ化の際に使用できる事前設定済みのポリシーがいくつか付属しています。 特定のSWF許可リスト権限など、追加のポリシー設定が必要な場合は、含まれているPrimetime DRM Policy Managerを使用して、カスタムポリシーを生成できます。

>[!NOTE]
>
>すべてのポリシーは、（ユーザー名パスワードやカスタムではなく）匿名認証を使用する必要があります。カスタム認証/権利付与ワークフローが使用されているかどうかに関係ありません。

Policy Managerには[!DNL flashaccesstools.properties]設定ファイルが含まれています。この設定ファイルは、Primetime Cloud DRMサービスがサポートする設定可能なポリシーオプションのみを公開するように変更されています。 Primetime Cloud DRMサービスでサポートされていないポリシーオプションを設定すると、ライセンス取得エラーが発生します。 Primetime DRMポリシーマネージャーの使用に関する詳細は、次を参照してください。[Primetime DRM参照の実装：Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager)。

新しいポリシーを作成するには、必要に応じて[!DNL flashaccesstools.properties]ファイルを更新し、次のコマンドを使用します。

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## カスタム認証/エンタイトルメント{#create-policies-dynamically-for-custom-auth-entitlement}のポリシーを動的に作成

Primetime Cloud DRMのカスタム認証/権利付与を使用し、（事前に生成されたプールからポリシーを取り込むのではなく）各ライセンスリクエストに対して新しいDRMポリシーを動的に作成する場合、AdobeではPrimetime DRM Java SDKを直接使用することをお勧めします。 Java SDKを直接使用する方が[!DNL AdobePolicyManager.jar]ツールより高速です。&lt;a0/>ツールを使用すると、ポリシーファイルが自動的にディスクに出力され、ディスクI/Oのオーバーヘッドが発生します。

Java SDKを使用したサンプルコードは、[!DNL CreatePolicy.java]および[!DNL CreatePolicyWithOutputProtection.java]という[!DNL /Primetime DRM PolicyManager/sampleCode/]ディレクトリにあります。 JavaDocおよびJava SDKに関するドキュメントは、[Adobe PrimetimeDRM SDKの概要](../../../digital-rights-management/drm-sdk-overview/overview.md)で参照できます。

サンプルを作成して実行するには、.javaファイルを。./libs/フォルダーにコピーし、次のコマンドを実行します。

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```

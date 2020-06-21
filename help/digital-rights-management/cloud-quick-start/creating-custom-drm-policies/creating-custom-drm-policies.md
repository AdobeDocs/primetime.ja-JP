---
seo-title: カスタムDRMポリシーの作成（オプション）
title: カスタムDRMポリシーの作成（オプション）
uuid: 701b51d9-6dde-4c21-bc5b-09e612582968
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# カスタムDRMポリシーの作成（オプション）{#create-custom-drm-policies-optional}

Primetime Cloud DRM保護キットには、パッケージ化の際に使用できる事前設定済みのポリシーがいくつか付属しています。 特定のSWF許可リスト権限など、追加のポリシー設定が必要な場合は、含まれているPrimetime DRM Policy Managerを使用してカスタムポリシーを生成できます。

>[!NOTE]
>
>すべてのポリシーは、（ユーザー名パスワードやカスタムではなく）匿名認証を使用する必要があります。カスタム認証/権利付与ワークフローが使用されているかどうかに関係ありません。

Policy Managerには [!DNL flashaccesstools.properties] 設定ファイルが含まれます。このファイルは、Primetime Cloud DRMサービスがサポートする設定可能なポリシーオプションのみを公開するように変更されています。 Primetime Cloud DRMサービスでサポートされていないポリシーオプションを設定すると、ライセンス取得エラーが発生します。 Primetime DRMポリシーマネージャーの使用に関する詳細は、次を参照してください。 [Primetime DRM参照の実装： Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager)。

新しいポリシーを作成するには、必要に応じて [!DNL flashaccesstools.properties] ファイルを更新し、次のコマンドを使用します。

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## カスタム認証/権利付与用のポリシーの動的な作成{#create-policies-dynamically-for-custom-auth-entitlement}

Primetime Cloud DRMのカスタム認証/権利付与を使用し、（事前に生成されたプールからポリシーを取り込むのではなく）各ライセンスリクエストに対して新しいDRMポリシーを動的に作成する場合は、Primetime DRM Java SDKを直接使用することをお勧めします。 Java SDKを直接使用する方が、ポリシーファイルをディスクに自動的に出力する [!DNL AdobePolicyManager.jar] ツールよりも高速で、ディスクI/Oのオーバーヘッドが発生します。

Java SDKを使用するサンプルコードは、 [!DNL /Primetime DRM PolicyManager/sampleCode/] およびという名前のディレクトリにあ [!DNL CreatePolicy.java] り [!DNL CreatePolicyWithOutputProtection.java]ます。 JavaDocおよびJava SDKのドキュメントは、Adobe Primetime DRM SDKの概要 [で確認できます。](../../../digital-rights-management/drm-sdk-overview/overview.md)

サンプルを作成して実行するには、.javaファイルを。./libs/フォルダーにコピーし、次のコマンドを実行します。

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```

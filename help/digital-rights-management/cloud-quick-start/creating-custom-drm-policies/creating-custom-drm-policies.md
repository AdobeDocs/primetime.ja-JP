---
title: カスタム DRM ポリシーの作成（オプション）
description: カスタム DRM ポリシーの作成（オプション）
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# カスタム DRM ポリシーの作成（オプション）{#create-custom-drm-policies-optional}

Primetime Cloud DRM 保護キットには、パッケージ化時に使用できる事前設定済みのポリシーがいくつか付属しています。 追加のポリシー設定 ( 特定のSWF許可リスト権限など ) が必要な場合は、付属の Primetime DRM Policy Manager を使用してカスタムポリシーを生成できます。

>[!NOTE]
>
>Custom Auth/Entitlement ワークフローが使用されているかどうかに関係なく、すべてのポリシーで、匿名認証（ユーザー名パスワードやカスタムではなく）を使用する必要があります。

Policy Manager に含まれる： [!DNL flashaccesstools.properties] 設定ファイル（Primetime Cloud DRM サービスがサポートする設定可能なポリシーオプションのみを公開するように変更） Primetime Cloud DRM サービスでサポートされていないポリシーオプションを設定すると、ライセンス取得エラーが発生します。 Primetime DRM Policy Manager の使用に関する詳細は、次を参照してください。 [Primetime DRM 参照実装：Policy Manager](https://help.adobe.com/en_US/primetime/drm/5.3/reference_implementations/index.html#concept-DRM_Policy_Manager).

新しいポリシーを作成するには、 [!DNL flashaccesstools.properties] 必要に応じてファイルを作成し、次のコマンドを使用します。

```
java -jar libs/AdobePolicyManager.jar new myPolicy.pol
```

## カスタム認証/権利付与用のポリシーを動的に作成{#create-policies-dynamically-for-custom-auth-entitlement}

Primetime Cloud DRM のカスタム認証/使用権限を使用していて、（事前に生成されたプールからポリシーをプルするのではなく）ライセンス要求ごとに新しい DRM ポリシーを動的に作成する場合は、Primetime DRM Java SDK を直接使用することをAdobeにお勧めします。 Java SDK を直接使用する方が、 [!DNL AdobePolicyManager.jar] ツールを使用して、ポリシー・ファイルを自動的にディスクに出力し、ディスクの I/O オーバーヘッドが発生します。

Java SDK を使用するサンプルコードは、 [!DNL /Primetime DRM PolicyManager/sampleCode/] ディレクトリ、名前 [!DNL CreatePolicy.java] および [!DNL CreatePolicyWithOutputProtection.java]. Java SDK の JavaDoc およびドキュメントについては、を参照してください。 [Adobe Primetime DRM SDK の概要](../../../digital-rights-management/drm-sdk-overview/overview.md)

サンプルをビルドして実行するには、.java ファイルを。./libs/フォルダーにコピーし、次のコマンドを実行します。

```
javac -cp adobe-flashaccess-sdk.jar:. CreatePolicy.java
java -cp adobe-flashaccess-sdk.jar:. CreatePolicy
```

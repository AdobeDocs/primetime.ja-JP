---
title: コンピューター資格情報の失効
description: コンピューター資格情報の失効
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# コンピューター資格情報の失効{#revoking-machine-credentials}

Adobeは、問題が発生することがわかっているコンピューターの資格情報を失効させるためのCRLを管理しています。 このCRLは、SDKによって自動的に適用されます。 ライセンスサーバーにライセンスを発行しない追加のコンピューターがある場合は、マシン失効リストを作成し、除外するマシントークンの発行者名とシリアル番号を追加できます（マシン証明書の発行者名とシリアル番号を取得するには`MachineToken.getMachineTokenId()`を使用します）。

マシンの資格情報を失効させるには、`RevocationListFactory`オブジェクトを使用します。 失効リストを作成するには、既存の失効リストを読み込み、Java APIを使用してマシントークンが失効したかどうかを確認します。次の手順を実行します。

1. 開発環境を設定し、プロジェクト内の[開発環境の設定](../../protecting-content/setting-up-the-sdk/setup-dev-env.md)で説明されているすべてのJARファイルを含めます。
1. `ServerCredentialFactory`インスタンスを作成して、署名に必要な資格情報を読み込みます。 ライセンスサーバー資格情報は、失効リストへの署名に使用されます。
1. `RevocationListFactory`インスタンスを作成します。
1. `IssuerAndSerialNumber`オブジェクトを使用して、取り消すマシントークンの発行者とシリアル番号を指定します。 すべてのAdobe PrimetimeDRMリクエストには、マシントークンが含まれています。
1. 先ほど作成した`IssuerAndSerialNumber`オブジェクトを使用して`RevocationList`オブジェクトを作成し、`RevocationListFactory.addRevocationEntry()`に渡して失効リストに追加します。 `RevocationListFactory.generateRevocationList()`を呼び出して、新しい失効リストを生成します。

1. 失効リストを保存するには、`RevocationList.getBytes()`を呼び出して失効メッセージをシリアル化します。 リストを読み込むには、`RevocationListFactory.loadRevocationList()`を呼び出し、シリアライズされたリストを渡します。

1. 署名が有効で、リストが正しいライセンスサーバーによって署名されていることを確認するには、`RevocationList.verifySignature()`を呼び出します。
1. エントリが失効したかどうかを確認するには、`IssuerAndSerialNumber`オブジェクトを`RevocationList.isRevoked()`に渡します。 また、失効リストを`HandlerConfiguration`に渡して、SDKがすべての認証およびライセンス要求に対して失効リストを強制するようにすることもできます。

既存の`RevocationList`にエントリを追加するには、既存の失効リストを読み込みます。 新しい`RevocationListFactory`インスタンスを作成し、必ずCRL番号を増やしてください。 `RevocationListFactioryEntries.addRevocationEntries`を呼び出して、古いリストのすべてのエントリを新しいリストに追加します。 `RevocationListFactory.addRevocationEntry`を呼び出して、新しい失効エントリをRevocationListに追加します。

失効リストの作成方法、既存の失効リストの読み込み方法、およびマシントークンが失効したかどうかを確認する方法を示すサンプルコードについては、リファレンス実装のコマンドラインツール[!DNL samples]の`com.adobe.flashaccess.samples.revocation.CreateRevocationList`を参照してください。

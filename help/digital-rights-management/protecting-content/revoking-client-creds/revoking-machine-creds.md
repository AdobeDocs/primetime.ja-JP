---
title: コンピューターの資格情報の取り消し
description: コンピューターの資格情報の取り消し
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# コンピューターの資格情報の取り消し {#revoking-machine-credentials}

Adobeは、侵入されることが知られているマシンの資格情報を失効するための CRL を管理します。 この CRL は、SDK によって自動的に適用されます。 ライセンスサーバーにライセンスを発行したくない追加のマシンがある場合は、マシン失効リストを作成し、除外するマシントークンの発行者名とシリアル番号を追加できます ( `MachineToken.getMachineTokenId()` （コンピュータ証明書の発行者名とシリアル番号を取得する）。

マシンの資格情報を取り消すには、 `RevocationListFactory` オブジェクト。 失効リストを作成し、既存の失効リストを読み込み、Java API を使用してコンピュータートークンが失効したかどうかを確認するには、次の手順を実行します。

1. 開発環境を設定し、 [開発環境の設定](../../protecting-content/setting-up-the-sdk/setup-dev-env.md) を選択します。
1. の作成 `ServerCredentialFactory` 署名に必要な資格情報を読み込むためのインスタンスです。 ライセンスサーバーの資格情報は、失効リストへの署名に使用されます。
1. の作成 `RevocationListFactory` インスタンス。
1. 取り消すマシントークンの発行者とシリアル番号を、 `IssuerAndSerialNumber` オブジェクト。 すべてのAdobe Primetime DRM リクエストにはマシントークンが含まれています。
1. の作成 `RevocationList` オブジェクトを `IssuerAndSerialNumber` 作成したオブジェクトを失効リストに追加し、次の場所に渡して失効リストに追加します。 `RevocationListFactory.addRevocationEntry()`. を呼び出して新しい失効リストを生成します `RevocationListFactory.generateRevocationList()`.

1. 失効リストを保存するには、を呼び出すことで失効リストをシリアライズします `RevocationList.getBytes()`. リストを読み込むには、 `RevocationListFactory.loadRevocationList()` シリアル化リストを渡します。

1. 署名が有効で、リストが正しいライセンスサーバーによって署名されたことを確認するには、 `RevocationList.verifySignature()`.
1. エントリが取り消されたかどうかを確認するには、 `IssuerAndSerialNumber` ～に向かう `RevocationList.isRevoked()`. 失効リストは、 `HandlerConfiguration` をクリックすると、すべての認証およびライセンス要求に対して失効リストが SDK によって強制的に適用されます。

既存のエントリにエントリを追加するには `RevocationList`、既存の失効リストを読み込みます。 新規作成 `RevocationListFactory` インスタンスを作成し、必ず CRL 番号を増やしてください。 通話 `RevocationListFactioryEntries.addRevocationEntries` をクリックして、古いリストから新しいリストにすべてのエントリを追加します。 通話 `RevocationListFactory.addRevocationEntry` をクリックして、新しい失効エントリを RevocationList に追加します。

失効リストの作成、既存の失効リストの読み込み、およびコンピュータートークンが失効しているかどうかの確認方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.revocation.CreateRevocationList` （「参照実装」コマンドラインツール） [!DNL samples] ディレクトリ。

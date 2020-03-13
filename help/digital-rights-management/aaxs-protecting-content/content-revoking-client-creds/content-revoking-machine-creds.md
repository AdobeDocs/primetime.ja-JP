---
seo-title: コンピューター資格情報の失効
title: コンピューター資格情報の失効
uuid: 16119ff9-8147-4fe0-9744-a705d94a9400
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コンピューター資格情報の失効{#revoking-machine-credentials}

アドビは、問題が発生する可能性があるコンピューターの資格情報を失効するためのCRLを管理しています。 このCRLはSDKによって自動的に適用されます。 ライセンスサーバーからライセンスを発行しないマシンが他にもある場合は、マシン失効リストを作成し、除外するマシントークンの発行者名とシリアル番号を追加できます（マシン証明書の発行者名とシリアル番号を取得するために使用します）。 `MachineToken.getMachineTokenId()`

マシンの資格情報を取り消すには、オブジェクトの使用が必 `RevocationListFactory` 要です。 失効リストを作成し、既存の失効リストを読み込み、Java APIを使用してコンピュータートークンが失効したかどうかを確認するには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」に記載されてい [るすべてのJARファイルを](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) 含めます。
1. 署名に必要な `ServerCredentialFactory` 資格情報を読み込むためのインスタンスを作成します。 ライセンスサーバーの秘密鍵証明書は、失効リストへの署名に使用されます。
1. インスタンスを作 `RevocationListFactory` 成します。
1. オブジェクトを使用して、失効させるマシントークンの発行者とシリアル番号を指定 `IssuerAndSerialNumber` します。 すべてのAdobe Accessリクエストには、1つのマシントークンが含まれます。
1. 作成したオ `RevocationList` ブジェクトを `IssuerAndSerialNumber` 使用してオブジェクトを作成し、に渡して失効リストに追加します `RevocationListFactory.addRevocationEntry()`。 を呼び出して、新しい失効リストを生成しま `RevocationListFactory.generateRevocationList()`す。
1. 失効リストを保存するには、を呼び出して、失効リストをシリアライズしま `RevocationList.getBytes()`す。 リストを読み込むには、シリアライズされたリ `RevocationListFactory.loadRevocationList()` ストを呼び出して渡す必要があります。
1. 署名が有効で、リストが正しいライセンスサーバーによって署名されていることを、を呼び出して確認しま `RevocationList.verifySignature()`す。
1. エントリが失効したかどうかを確認するには、オブジェクトを `IssuerAndSerialNumber` に渡しま `RevocationList.isRevoked()`す。 また、失効リストをに渡して、SDKがすべての認 `HandlerConfiguration` 証およびライセンス要求に対して失効リストを強制するように設定することもできます。

既存の失効リストにエントリを追加するに `RevocationList`は、既存の失効リストを読み込みます。 新しいインスタンス `RevocationListFactory` を作成し、必ずCRL番号を増分してください。 を呼び `RevocationListFactioryEntries.addRevocationEntries` 出して、古いリストのすべてのエントリを新しいリストに追加します。 RevocationListに新 `RevocationListFactory.addRevocationEntry` しい失効エントリを追加するための呼び出し。

失効リストの作成、既存の失効リストの読み込み、およびコンピュータートークンの失効の確認の方法を示すサンプルコードについては、リファレンス実装コマンドラインツールの「 `com.adobe.flashaccess.samples.revocation.CreateRevocationList` samples」ディレクトリを参照してください。

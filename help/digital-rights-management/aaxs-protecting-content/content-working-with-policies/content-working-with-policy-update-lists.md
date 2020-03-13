---
seo-title: ポリシー更新リストの操作
title: ポリシー更新リストの操作
uuid: 583abb31-5c80-43f2-bc3d-a2300f61c4ea
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ポリシー更新リストの操作{#working-with-policy-update-lists}

ポリシーに関する情報を保存するためのデータベースへのアクセス権を持たないライセンスサーバーの場合は、ポリシー更新リストを使用して、更新されたポリシーをライセンスサーバーに通知することができます。 ポリシー更新リストには、更新されたバージョンのポリシーまたは失効したポリシーIDのリストが含まれる場合があります。 でポリシー更新リストが指定されている場合、SDK `HandlerConfiguration`は、ライセンスの発行時にこのリストを強制的に適用します。

また、コンテンツ所有者または配布者が特定のポリシーに基づいてライセンスの発行を中止する場合は、ポリシーを取り消すこともできます。 ポリシー更新リストは、SDKでポリシーの失効を強制するために使用できます。 ポリシー更新リストは、更新されたポリシーのリストをSDKに提供するためにも使用できます。 ポリシーを失効しても、既に発行されているライセンスは失効しません。 このポリシーに基づいて追加のライセンスが発行されるのを防ぐだけです。

ポリシー更新リストの操作には、オブジェクトの使用が含ま `PolicyUpdateListFactory` れます。 ポリシー更新リストを作成するには、既存のポリシー更新リストを読み込み、Java APIを使用してポリシーが更新または失効したかどうかを確認するには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」で説明されているすべてのJARファイルを含めます。
1. 署名に必要な `ServerCredentialFactory` 資格情報を読み込むためのインスタンスを作成します。
1. 作成したを使 `PolicyUpdateListFactory` 用してインスタンス `ServerCredential` を作成します。
1. 取り消すポリシーIDを指定します。
1. 作成したポ `PolicyRevocationEntry` リシーIDを使用し `String` てオブジェクトを作成し、に渡してポリシー更新リストに追加します `PolicyUpdateListFactory.addRevocationEntry()`。 を呼び出して、新しいポリシー更新リストを生成しま `PolicyUpdateListFactory.generatePolicyUpdateList()`す。 同様に、更新されたポリシーは、を使用してリストに追加できま `PolicyUpdateEntry`す。
1. ポリシー更新リストが既に存在する場合は、を呼び出して読み込むためにシリアライズできま `PolicyUpdateList.getBytes()`す。 リストを読み込むには、シリアライズされたリ `PolicyUpdateListFactory.loadPolicyUpdateList()` ストを呼び出して渡す必要があります。
1. 署名が有効で、リストが正しいライセンスサーバー証明書で署名されていることを、を呼び出して確認しま `PolicyUpdateList.verifySignature()`す。
1. エントリが失効したかどうかを確認するには、ポリシーIDをに渡 `String` しま `PolicyUpdateList.isRevoked()`す。 または、リストをに渡し、ライセン `HandlerConfiguration` スの発行時にリストを適用できます。

既存のポリシーにエントリを追加するには、既 `PolicyUpdateList`存のポリシー更新リストを読み込みます。 新しいインスタンスを作 `PolicyUpdateListFactory` 成します。 Pを呼び出し `olicyUpdateListFactory.addEntries` て、古いリストのすべてのエントリを新しいリストに追加します。 PolicyUpdateListに新し `PolicyUpdateListFactory.addRevocationEntry` い失効エ `addUpdatedEntry` ントリまたは更新エントリを追加するために、またはを呼び出します。

ポリシー更新リストの作成、既存のポリシー更新リストの読み込み、ポリシーが失効したかどうかの確認の方法を示すサンプルコードについては、『リファレンス実装コマンドラインツール `com.adobe.flashaccess.samples.policyupdatelist``.CreatePolicyUpdateList` 』の「samples」ディレクトリを参照してください。

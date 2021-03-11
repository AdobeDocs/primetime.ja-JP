---
title: ポリシー更新リストの操作
description: ポリシー更新リストの操作
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ポリシー更新リストの操作{#working-with-policy-update-lists}

ポリシーに関する情報を保存するためのデータベースへのアクセス権を持たないライセンスサーバーの場合は、ポリシー更新リストを使用して、更新されたポリシーをライセンスサーバーに通知することができます。 ポリシーの更新リストには、ポリシーの更新バージョンまたは失効したポリシーIDのリストが含まれる場合があります。 `HandlerConfiguration`にポリシー更新リストが指定されている場合、SDKは、ライセンスの発行時にこのリストを強制します。

また、コンテンツ所有者または配布者が特定のポリシーに基づいてライセンスの発行を中止する場合は、ポリシーを失効させることもできます。 ポリシー更新リストは、SDKでポリシー失効を強制するために使用できます。 ポリシーの更新リストは、更新されたポリシーのリストをSDKに提供する場合にも使用できます。 ポリシーを失効しても、既に発行されているライセンスは失効しません。 これは、そのポリシーに基づいて追加のライセンスが発行されるのを防ぐだけです。

ポリシー更新リストの操作には、`PolicyUpdateListFactory`オブジェクトの使用が含まれます。 ポリシー更新リストを作成するには、既存のポリシー更新リストを読み込み、Java APIを使用してポリシーが更新されたか失効したかを確認します。次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内での開発環境の設定」に記載されているすべてのJARファイルを含めます。
1. `ServerCredentialFactory`インスタンスを作成して、署名に必要な資格情報を読み込みます。
1. 作成した`ServerCredential`を使用して`PolicyUpdateListFactory`インスタンスを作成します。
1. 取り消すポリシーIDを指定します。
1. 先ほど作成したポリシーID `String`を使用して`PolicyRevocationEntry`オブジェクトを作成し、`PolicyUpdateListFactory.addRevocationEntry()`に渡してポリシー更新リストに追加します。 `PolicyUpdateListFactory.generatePolicyUpdateList()`を呼び出して、新しいポリシー更新リストを生成します。 同様に、更新されたポリシーは`PolicyUpdateEntry`を使用してリストに追加できます。
1. ポリシー更新リストが既に存在する場合は、`PolicyUpdateList.getBytes()`を呼び出すことで、読み込み用にシリアル化できます。 リストを読み込むには、`PolicyUpdateListFactory.loadPolicyUpdateList()`を呼び出し、シリアライズされたリストを渡します。
1. 署名が有効で、リストが正しいライセンスサーバー証明書によって署名されていることを確認するには、`PolicyUpdateList.verifySignature()`を呼び出します。
1. エントリが失効したかどうかを確認するには、ポリシーID `String`を`PolicyUpdateList.isRevoked()`に渡します。 または、リストを`HandlerConfiguration`に渡し、ライセンスが発行される際に強制されます。

既存の`PolicyUpdateList`にエントリを追加するには、既存のポリシー更新リストを読み込みます。 新しい`PolicyUpdateListFactory`インスタンスを作成します。 P `olicyUpdateListFactory.addEntries`を呼び出して、古いリストのすべてのエントリを新しいリストに追加します。 `PolicyUpdateListFactory.addRevocationEntry`または`addUpdatedEntry`を呼び出して、新しい失効エントリまたは更新エントリをPolicyUpdateListに追加します。

ポリシー更新リストの作成、既存のポリシー更新リストの読み込み、ポリシーが失効したかどうかを確認する方法を示すサンプルコードについては、リファレンス実装のコマンドラインツールの&quot;samples&quot;ディレクトリの`com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList`を参照してください。

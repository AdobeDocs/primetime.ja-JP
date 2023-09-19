---
title: ポリシー更新リストの操作
description: ポリシー更新リストの操作
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ポリシー更新リストの操作{#working-with-policy-update-lists}

ポリシーに関する情報を保存するためのデータベースにアクセスできないライセンスサーバの場合は、ポリシー更新リストを使用して、更新されたポリシーをライセンスサーバに通知することができます。 ポリシー更新リストには、ポリシーの更新バージョンまたは失効したポリシー ID のリストが含まれる場合があります。 ポリシー更新リストが `HandlerConfiguration`に設定すると、SDK は、ライセンスを発行する際にこのリストを強制的に適用します。

コンテンツ所有者やディストリビューターが特定のポリシーに基づくライセンスの発行を中止する場合も、ポリシーが失効する可能性があります。 ポリシー更新リストは、SDK でポリシーの失効を強制するために使用できます。 ポリシー更新リストは、更新されたポリシーのリストを SDK に提供する場合にも使用できます。 ポリシーを取り消しても、既に発行されたライセンスは失われません。 このポリシーに基づく追加のライセンスの発行を禁止するだけです。

ポリシー更新リストの使用には、 `PolicyUpdateListFactory` オブジェクト。 ポリシー更新リストを作成し、既存のポリシー更新リストを読み込み、Java API を使用してポリシーが更新または取り消されたかどうかを確認するには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内での開発環境の設定で説明されているすべての JAR ファイルを含めます。
1. の作成 `ServerCredentialFactory` 署名に必要な資格情報を読み込むためのインスタンスです。
1. の作成 `PolicyUpdateListFactory` インスタンスを `ServerCredential` 作成済みです。
1. 取り消すポリシー ID を指定します。
1. の作成 `PolicyRevocationEntry` ポリシー ID を使用するオブジェクト `String` 作成したばかりで、次の場所に渡してポリシー更新リストに追加します： `PolicyUpdateListFactory.addRevocationEntry()`. を呼び出して新しいポリシー更新リストを生成します `PolicyUpdateListFactory.generatePolicyUpdateList()`. 同様に、更新されたポリシーを `PolicyUpdateEntry`.
1. ポリシー更新リストが既に存在する場合は、を呼び出すことで、読み込むためにシリアル化できます `PolicyUpdateList.getBytes()`. リストを読み込むには、 `PolicyUpdateListFactory.loadPolicyUpdateList()` シリアル化リストを渡します。
1. 署名が有効であり、リストが正しいライセンスサーバー証明書によって署名されていることを、 `PolicyUpdateList.verifySignature()`.
1. エントリが失効したかどうかを確認するには、ポリシー ID を渡します `String` into `PolicyUpdateList.isRevoked()`. または、リストを `HandlerConfiguration` ライセンスが発行されるときに適用されます。

既存のエントリにエントリを追加するには `PolicyUpdateList`、既存のポリシー更新リストを読み込みます。 新規作成 `PolicyUpdateListFactory` インスタンス。 呼び出し P `olicyUpdateListFactory.addEntries` をクリックして、古いリストから新しいリストにすべてのエントリを追加します。 通話 `PolicyUpdateListFactory.addRevocationEntry` または `addUpdatedEntry` 新しい失効または更新エントリを PolicyUpdateList に追加する場合。

ポリシー更新リストの作成、既存のポリシー更新リストの読み込み、ポリシーが失効しているかどうかの確認方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` 「リファレンス実装」コマンドラインツールの「samples」ディレクトリ。

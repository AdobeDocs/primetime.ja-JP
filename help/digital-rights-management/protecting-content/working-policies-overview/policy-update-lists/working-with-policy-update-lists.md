---
seo-title: DRMポリシーの更新リストの操作
title: DRMポリシーの更新リストの操作
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# DRMポリシー更新リスト{#drm-policy-update-lists}

コンテンツをパッケージ化した後にDRMポリシーの使用規則を更新する場合、更新されたDRMポリシーを使用するライセンスを発行するには、ライセンスサーバーに最新バージョンが必要です。 これを達成する1つの方法は、DRMポリシーの更新リストを通じてです。

DRMポリシーの更新リストは、更新または失効したDRMポリシーのリストを含むファイルで表されます。 DRMポリシーを更新する場合は常に、新しいDRMポリシー更新リストを生成し、定期的にリストをすべてのライセンスサーバーにプッシュする必要があります。

## DRMポリシー更新リストの操作{#working-with-drm-policy-update-lists}

DRMポリシーに関する情報を保存するためのデータベースへのアクセス権を持たないライセンスサーバーの場合は、DRMポリシー更新リストを使用して、更新されたDRMポリシーをライセンスサーバーに通知することができます。 DRMポリシーの更新リストには、更新されたDRMポリシーのバージョンまたは失効したDRMポリシーIDのリストが含まれる場合があります。 ポリシーの更新リストが`HandlerConfiguration`に含まれている場合、SDKは、このリストをライセンスの発行時に適用します。

コンテンツ所有者または配布者が特定のDRMポリシーに基づくライセンスの発行を中止する場合は、DRMポリシーを失効させることもできます。 DRMポリシーの更新リストを使用して、SDKでDRMポリシーの失効を強制できます。 DRMポリシーの更新リストを適用して、更新されたDRMポリシーのリストをSDKに提供することもできます。

>[!NOTE]
>
>DRMポリシーを無効にした場合、既に発行されているライセンスは自動的に無効にはなりません。 このDRMポリシーに基づいて追加のライセンスが発行されるのを防ぐだけです。

## ポリシー更新リストの更新{#update-policy-update-lists}

DRMポリシーの更新リストを使用するには、`PolicyUpdateListFactory`オブジェクトを使用します。 DRMポリシーの更新リストを作成する場合は、既存のDRMポリシーの更新リストを読み込み、Java APIを使用してDRMポリシーが更新されたか失効したかを確認する必要があります。

DRMポリシーの更新リストを使用するには：

1. 開発環境を設定し、プロジェクトで開発環境を設定する際に含まれるすべてのJARファイルを含めます。
1. `ServerCredentialFactory`インスタンスを作成して、署名に必要な資格情報を読み込みます。
1. 作成した`ServerCredential`を使用して`PolicyUpdateListFactory`インスタンスを作成します。
1. 失効させるDRMポリシーIDを指定します。
1. 作成したDRMポリシーID `String`を使用して`PolicyRevocationEntry`オブジェクトを作成し、`PolicyUpdateListFactory.addRevocationEntry()`に渡してDRMポリシー更新リストに追加します。
1. `PolicyUpdateListFactory.generatePolicyUpdateList()`を呼び出して、新しいDRMポリシー更新リストを生成します。

   同様に、`PolicyUpdateEntry`を使用して、リストに対するDRMポリシーを更新できます。
1. DRMポリシーの更新リストが既に存在する場合は、`PolicyUpdateList.getBytes()`を呼び出して、読み込み用にシリアル化できます。

   リストを読み込むには、`PolicyUpdateListFactory.loadPolicyUpdateList()`を呼び出し、シリアライズされたリストで渡します。
1. 署名が有効で、リストが正しいライセンスサーバー証明書によって署名されていることを確認するには、`PolicyUpdateList.verifySignature()`を呼び出します。
1. DRMポリシーID `String`を`PolicyUpdateList.isRevoked()`に渡して、エントリが失効したことを確認します。

   または、リストを`HandlerConfiguration`に渡して、ライセンスが発行されるたびに&lt;a0/>に適用することもできます。
既存の`PolicyUpdateList`にさらにエントリを追加する場合は、既存のDRMポリシー更新リストを読み込む必要があります。 したがって、新しいDRM `PolicyUpdateListFactory`インスタンスを作成する必要があります。 `PolicyUpdateListFactory.addEntries`を呼び出して、古いリストのすべてのエントリを新しいリストに追加します。 `PolicyUpdateListFactory.addRevocationEntry`または`addUpdatedEntry`を呼び出して、新しい失効エントリまたは更新エントリをDRM PolicyUpdateListに追加します。

DRMポリシーの更新リストの作成方法を示すサンプルコードについては、*リファレンス実装のコマンドラインツール* [!DNL samples]ディレクトリの`com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList`を参照してください。

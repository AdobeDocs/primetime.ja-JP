---
seo-title: DRMポリシーの更新リストの操作
title: DRMポリシーの更新リストの操作
uuid: 41f89671-81c6-4d3d-ac31-9c2a1980517a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# DRMポリシーの更新リスト {#drm-policy-update-lists}

コンテンツをパッケージ化した後にDRMポリシーの使用ルールを更新する場合、更新されたDRMポリシーを使用するライセンスを発行するには、ライセンスサーバーが最新バージョンである必要があります。 これを達成する1つの方法は、DRMポリシーの更新リストを通じてです。

DRMポリシーの更新リストは、更新または失効したDRMポリシーのリストを含むファイルで表されます。 DRMポリシーを更新する場合は、必ず新しいDRMポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュする必要があります。

## DRMポリシーの更新リストの操作 {#working-with-drm-policy-update-lists}

DRMポリシーに関する情報を保存するためのデータベースへのアクセス権を持たないライセンスサーバーの場合は、DRMポリシー更新リストを使用して、更新されたDRMポリシーをライセンスサーバーに通知することができます。 DRMポリシーの更新リストには、更新されたバージョンのDRMポリシーや、失効したDRMポリシーIDのリストが含まれる場合があります。 にポリシー更新リストが含まれている場合、SDK `HandlerConfiguration`はライセンスを発行する際にこのリストを適用します。

また、コンテンツの所有者または配布者が特定のDRMポリシーに基づくライセンスの発行を中止する場合は、DRMポリシーを無効にすることもできます。 DRMポリシーの更新リストは、SDKでDRMポリシーの失効を強制するために使用できます。 また、DRMポリシーの更新リストを適用して、更新されたDRMポリシーのリストをSDKに提供することもできます。

>[!NOTE]
>
>DRMポリシーを失効させても、既に発行されているライセンスは自動的には取り消されません。 このDRMポリシーに基づいて追加のライセンスが発行されるのを防ぐだけです。

## ポリシー更新リストの更新{#update-policy-update-lists}

DRMポリシーの更新リストを使用する場合は、オブジェクトを使用 `PolicyUpdateListFactory` します。 DRMポリシーの更新リストを作成する場合は、既存のDRMポリシーの更新リストを読み込み、Java APIを使用してDRMポリシーが更新されたか失効したかを確認する必要があります。

DRMポリシーの更新リストを使用するには：

1. 開発環境を設定し、プロジェクトで開発環境を設定する際に含めるすべてのJARファイルを含めます。
1. 署名に必要な `ServerCredentialFactory` 資格情報を読み込むためのインスタンスを作成します。
1. 作成したイ `PolicyUpdateListFactory` ンスタンスを使用し `ServerCredential` てインスタンスを作成します。
1. 失効するDRMポリシーIDを指定します。
1. 作成したDRM `PolicyRevocationEntry` ポリシーIDを使用してオ `String` ブジェクトを作成し、に渡してDRMポリシー更新リストに追加します `PolicyUpdateListFactory.addRevocationEntry()`。
1. を呼び出して、新しいDRMポリシー更新リストを生成しま `PolicyUpdateListFactory.generatePolicyUpdateList()`す。

   同様に、を使用して、DRMポリシーをリストに更新できま `PolicyUpdateEntry`す。
1. DRMポリシーの更新リストが既に存在する場合は、を呼び出して読み込むためにシリアライズできま `PolicyUpdateList.getBytes()`す。

   リストを読み込むには、を呼び出し `PolicyUpdateListFactory.loadPolicyUpdateList()` てシリアル化されたリストに渡します。
1. 署名が有効で、リストが正しいライセンスサーバー証明書で署名されていることを、を呼び出して確認しま `PolicyUpdateList.verifySignature()`す。
1. DRMポリシーIDをに渡して、 `String` エント `PolicyUpdateList.isRevoked()` リが失効したことを確認します。

   または、ライセンスが発行されるたびにリ `HandlerConfiguration` ストが適用される場所にリストを渡すこともできます。
既存のDRMポリシーの更新リストをさらに追加す `PolicyUpdateList`る場合は、既存のDRMポリシーの更新リストを読み込む必要があります。 したがって、新しいDRMインスタンスを作成する必要が `PolicyUpdateListFactory` あります。 を呼び `PolicyUpdateListFactory.addEntries` 出して、古いリストのすべてのエントリを新しいリストに追加します。 DRM PolicyUpdateList `PolicyUpdateListFactory.addRevocationEntry` に新しい失 `addUpdatedEntry` 効または更新エントリを追加するために、またはを呼び出します。

DRMポリシーの更新リストの作成方法を示すサンプルコードについては、参照実装コマンドラインツール `com.adobe.flashaccess.samples.policyupdatelist``.CreatePolicyUpdateList` ( *Reference Implementation Command Line Tools* )ディレクトリの [!DNL samples] を参照してください。

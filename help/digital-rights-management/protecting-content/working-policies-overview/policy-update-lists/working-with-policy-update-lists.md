---
title: DRM ポリシーの更新リストの操作
description: DRM ポリシーの更新リストの操作
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# DRM ポリシーの更新リスト {#drm-policy-update-lists}

コンテンツをパッケージ化した後に DRM ポリシーで使用ルールを更新する場合、更新された DRM ポリシーを使用するライセンスを発行する前に、ライセンスサーバーが最新バージョンになっている必要があります。 これを実現する 1 つの方法は、DRM ポリシーの更新リストを通じてです。

DRM ポリシー更新リストは、更新または取り消された DRM ポリシーのリストを含むファイルで表されます。 DRM ポリシーを更新する場合は、新しい DRM ポリシー更新リストを生成し、定期的にすべてのライセンスサーバーにリストをプッシュする必要があります。

## DRM ポリシーの更新リストの操作 {#working-with-drm-policy-update-lists}

DRM ポリシーに関する情報を保存するためのデータベースにアクセスできないライセンスサーバーの場合は、DRM ポリシー更新リストを使用して、更新された DRM ポリシーをライセンスサーバーに通知する必要があります。 DRM ポリシーの更新リストには、更新されたバージョンの DRM ポリシー、または取り消された DRM ポリシー ID のリストが含まれる場合があります。 ポリシー更新リストが `HandlerConfiguration`を指定した場合、SDK はライセンスを発行する際にこのリストを強制します。

コンテンツの所有者またはディストリビューターが特定の DRM ポリシーに基づくライセンスの発行を中止する場合は、DRM ポリシーを失効させることもできます。 DRM ポリシーの更新リストは、SDK で DRM ポリシーの失効を強制するために使用できます。 DRM ポリシーの更新リストを適用して、更新された DRM ポリシーのリストを SDK に提供することもできます。

>[!NOTE]
>
>DRM ポリシーを失効させる場合、既に発行されているライセンスは自動的に失効されません。 これは、その DRM ポリシーに基づいて追加のライセンスが発行されるのを防ぐだけです。

## ポリシー更新リストの更新{#update-policy-update-lists}

DRM ポリシーの更新リストを使用する場合、 `PolicyUpdateListFactory` オブジェクト。 DRM ポリシーの更新リストを作成する場合は、既存の DRM ポリシーの更新リストを読み込み、Java API を使用して DRM ポリシーが更新されたか取り消されたかを確認する必要があります。

DRM ポリシーの更新リストを操作するには：

1. 開発環境を設定し、プロジェクトで開発環境を設定する際に含まれるすべての JAR ファイルを含めます。
1. の作成 `ServerCredentialFactory` 署名に必要な資格情報を読み込むインスタンスです。
1. の作成 `PolicyUpdateListFactory` インスタンスを `ServerCredential` 作成した
1. 失効させる DRM ポリシー ID を指定します。
1. の作成 `PolicyRevocationEntry` オブジェクトに対して DRM ポリシー ID を使用します。 `String` 作成した後、DRM ポリシーの更新リストに追加するために、 `PolicyUpdateListFactory.addRevocationEntry()`.
1. を呼び出して新しい DRM ポリシーの更新リストを生成 `PolicyUpdateListFactory.generatePolicyUpdateList()`.

   同様に、 `PolicyUpdateEntry`.
1. DRM ポリシーの更新リストが既に存在する場合は、を呼び出すことで、読み込むためにシリアル化できます `PolicyUpdateList.getBytes()`.

   リストを読み込むには、 `PolicyUpdateListFactory.loadPolicyUpdateList()` シリアル化されたリストに渡します。
1. 署名が有効で、リストが正しいライセンスサーバー証明書によって署名されていることを、 `PolicyUpdateList.verifySignature()`.
1. DRM ポリシー ID を渡す `String` into `PolicyUpdateList.isRevoked()` エントリが失効したことを確認するには、をクリックします。

   または、リストをに渡すこともできます。 `HandlerConfiguration` ここでは、ライセンスが発行されるたびに適用されます。
既存のエントリにさらにエントリを追加する場合 `PolicyUpdateList`既存の DRM ポリシー更新リストを読み込む必要があります。 したがって、新しい DRM を作成する必要があります `PolicyUpdateListFactory` インスタンス。 通話 `PolicyUpdateListFactory.addEntries` をクリックして、古いリストから新しいリストにすべてのエントリを追加します。 通話 `PolicyUpdateListFactory.addRevocationEntry` または `addUpdatedEntry` をクリックして、新しい失効または更新エントリを DRM PolicyUpdateList に追加します。

DRM ポリシーの更新リストの作成方法を示すサンプルコードについては、 `com.adobe.flashaccess.samples.policyupdatelist` `.CreatePolicyUpdateList` （内） *参照実装コマンドラインツール* [!DNL samples] ディレクトリ。

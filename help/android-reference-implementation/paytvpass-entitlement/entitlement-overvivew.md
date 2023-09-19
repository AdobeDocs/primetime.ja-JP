---
description: エンタイトルメントマネージャーは、Primetime 認証実装をサポートする機能マネージャーです。
title: Entitlement Manager の概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Entitlement Manager の概要 {#entitlement-manager-overview}

エンタイトルメントマネージャーは、Primetime 認証実装をサポートする機能マネージャーです。

## 機能の概要

Android Primetime SDK リファレンス実装との Primetime 認証の統合により、新しい機能マネージャーがアプリケーションに追加されます。 ただし、他の多くの機能マネージャとは異なり、 *EntitlementManager は、アプリケーション全体の複数の場所で使用されます*. Primetime 認証をサポートするためにリファレンス実装に加えられた変更と追加の概要を次に示します。

### EntitlementManager クラス

The `EntitlementManager` クラスは、Primetime 認証 SDK とのすべての通信を処理し、さらに、権限付与ワークフローに必要なアプリケーションロジックをカプセル化します。 The `EntitlementManager`のパブリック API は、権限付与ワークフローを開始するためにアプリケーションで使用されますが、 `EntitlementMangerListener` インターフェイスは、アプリケーションが処理するコールバックメカニズムを提供します。 `EntitlementManger` イベント。

### EntitlementManger コールバック

参照実装のメインアクティビティ `CatalogActivity`は、次のインスタンスを作成します。 `EntitlementManagerListener` そして、 `EntitlementManager`. この方法で、 `EntitlementManager` は、アプリケーションの残りの部分に対して、必要な UI の更新を示す場合があります。 コールバックには、読み込みダイアログの表示/非表示、ステータスダイアログの表示、認証および認証アイコンの更新、認証成功時のビデオ再生の開始が含まれます。

### 権利ダイアログ

The `EntitlementDialogFragment` クラスは、クラスコンストラクターに渡されたエンタイトルメントステータスに基づいてダイアログメッセージを生成します。 このクラスは、認証成功メッセージおよびすべてのエラーメッセージに使用されます。 The `CatalogActivity` 特定のイベントを `EntitlementManager`. また、 `CatalogActivity` を実装する `EntitlementDialogListener` インターフェイス：ダイアログが閉じられたとき、またはユーザーが Primetime 認証サービスからログアウトしたときに通知するコールバックメソッドを含みます。

### コンテンツプロバイダーの選択とログイン

Primetime 認証を使用した認証時に、2 つの新しいアクティビティが追加されました。 `MvpdPickerActivity` および `MvpdLoginActivity`を使用すると、ユーザーはコンテンツプロバイダーを選択してログインできます。 これらのアクティビティは、どちらも `CatalogActivity` 経由 `EntitlementManager`. また、 `MvpdPickerActivity` および `MvpdLoginActivity` 結果をに返す `CatalogActivity` そしてそのために `CatalogActivity` は、 `Activity.onActivityResult` メソッド。

### ログインボタン

参照実装のメインアクティビティ `CatalogActivity`には、アクションバーに新しい「ログイン」ボタンが含まれます。 「ログイン」ボタンを使用すると、ユーザーは Primetime 認証を使用して認証を開始できます。 さらに、ユーザーは、再生用の保護されたビデオを選択することで認証を開始できます。 ログインボタンのアイコンとテキストは、ユーザーの認証状態と `CatalogActivity` には、ページが更新されたときにボタンのアイコンとテキストを更新するコードが含まれています。 これをおこなうには、 `CatalogActivity` 開始、呼び出し `EntitlementManager.checkAuthentication()` をクリックして、ユーザーの認証状態を更新します。

### コンテンツ使用権限

内 `CatalogView`を指定した場合、コンテンツのアイコンの上に新しいアイコンが表示され、そのコンテンツに対するユーザーの認証ステータスを示します。 例えば、ユーザーがビデオの視聴を事前に承認されている場合は、コンテンツの上に緑色の円のアイコンが表示されます。 ただし、ユーザーがビデオの視聴を事前に許可されていない場合は、キーアイコンが表示されます。 これらのアイコンの表示は、 `ContentTileAdapter`ただし、状態の更新は `CatalogActivity` ( `EntitlementManagerListener` が呼び出されます。

### コンテンツ再生

ビデオ再生に、 `EntitlementManager`. への呼び出し `EntitlementManager.getAuthorization()` 次の範囲内で発生 `CatalogView`. ビデオで認証が必要で、ユーザーが認証済みの場合、 `PlayerActivity` が `CatalogActivity`.

---
description: Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。
seo-description: Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。
seo-title: Entitlement Managerの概要
title: Entitlement Managerの概要
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Entitlement Managerの概要{#entitlement-manager-overview}

Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。

## 機能概要

Android Primetime SDKリファレンス実装とPrimetime認証の統合により、新しい機能マネージャーがアプリケーションに追加されました。 ただし、他の多くの機能マネージャーとは異なり、*EntitlementManagerは、アプリケーション*&#x200B;内の複数の場所で使用されます。 Primetime認証をサポートするためにリファレンス実装に加えられた変更点と追加点の概要を以下に示します。

### EntitlementManagerクラス

`EntitlementManager`クラスは、Primetime認証SDKとのすべての通信を処理し、エンタイトルメントワークフローに必要なアプリケーションロジックをカプセル化します。 `EntitlementManager`のパブリックAPIは、エンタイトルメントワークフローの開始にアプリケーションが使用します。一方、`EntitlementMangerListener`インターフェイスは、`EntitlementManger`イベントを処理するコールバックメカニズムを提供します。

### EntitlementMangerコールバック

参照実装のメインアクティビティ`CatalogActivity`は、`EntitlementManagerListener`のインスタンスを作成し、`EntitlementManager`に登録します。 このようにして、`EntitlementManager`は必要なUIの更新を他のアプリケーションに伝える場合があります。 コールバックには、読み込みダイアログの表示/非表示、ステータスダイアログの表示、認証および認証アイコンの更新、認証が成功した場合のビデオ再生の開始が含まれます。

### 権利付与ダイアログ

`EntitlementDialogFragment`クラスは、クラスコンストラクターに渡されたエンタイトルメントステータスに基づいてダイアログメッセージを生成します。 このクラスは、認証成功メッセージおよびすべてのエラーメッセージに使用されます。 `CatalogActivity`は、`EntitlementManager`から特定のイベントを受け取ると、エンタイトルメントダイアログを表示します。 さらに、`CatalogActivity`は、`EntitlementDialogListener`インターフェイスを実装します。このインターフェイスには、ダイアログが閉じられたときやユーザーがPrimetime認証サービスからログアウトしたときに通知するコールバックメソッドが含まれます。

### コンテンツプロバイダーの選択とログイン

Primetime認証での認証時に、`MvpdPickerActivity`と`MvpdLoginActivity`の2つの新しいアクティビティーでユーザーがコンテンツプロバイダーを選択してログインできるようになりました。 これらのアクティビティは両方とも`CatalogActivity`から`EntitlementManager`を介して起動されます。 また、`MvpdPickerActivity`と`MvpdLoginActivity`の両方が結果を`CatalogActivity`に返すので、`CatalogActivity`が`Activity.onActivityResult`メソッドを上書きする必要があります。

### サインインボタン

リファレンス実装のメインアクティビティ`CatalogActivity`には、アクションバーに新しい「サインイン」ボタンが含まれています。 「Sign In」ボタンを使用すると、ユーザーはPrimetime認証で認証を開始できます。 また、保護されたビデオを再生用に選択することで、ユーザが認証を開始することもできます。 「サインイン」ボタンのアイコンとテキストは、ユーザーの認証ステータスに応じて変化します。また、`CatalogActivity`には、ページが更新されたときにボタンのアイコンとテキストを更新するコードが含まれています。 これを行うには、`CatalogActivity`開始が`EntitlementManager.checkAuthentication()`を呼び出してユーザーの認証状態を更新します。

### コンテンツの権利付与

`CatalogView`内では、コンテンツのアイコンの上に新しいアイコンが表示され、そのコンテンツに対するユーザーの認証ステータスを伝えます。 例えば、ユーザーがビデオの表示を事前に承認されている場合、緑の円のアイコンがコンテンツの上に表示されます。 ただし、ユーザーがビデオの表示を事前に許可されていない場合は、キーアイコンが表示されます。 これらのアイコンの表示は`ContentTileAdapter`で処理されますが、`EntitlementManagerListener`内のコールバックが呼び出されると、`CatalogActivity`から状態の更新が開始されます。

### コンテンツ再生

ビデオ再生には、`EntitlementManager`による認証チェックが必要になりました。 `EntitlementManager.getAuthorization()`への呼び出しは`CatalogView`内で発生します。 ビデオに認証が必要で、ユーザーが認証されている場合、`PlayerActivity`は`CatalogActivity`から開始されます。


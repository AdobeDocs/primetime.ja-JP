---
description: Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。
seo-description: Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。
seo-title: Entitlement Managerの概要
title: Entitlement Managerの概要
uuid: b33dfae3-a132-4215-9992-80cbf4c87a61
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Entitlement Managerの概要 {#entitlement-manager-overview}

Entitlement Managerは、Primetime認証実装をサポートする機能マネージャーです。

## 機能の概要

Android Primetime SDKリファレンス実装とのPrimetime認証の統合により、新しい機能マネージャーがアプリケーションに追加されました。 ただし、他の多くの機能マネージャーとは異なり、EntitlementManager *はアプリケーション内の複数の場所で使用されます*。 次に、Primetime認証をサポートするためにリファレンス実装に加えられた変更と追加の概要を示します。

### EntitlementManagerクラス

このク `EntitlementManager` ラスは、Primetime認証SDKとのすべての通信を処理し、エンタイトルメントワークフローに必要なアプリケーションロジックをカプセル化します。 アプリケ `EntitlementManager`ーションは、エンタイトルメントワークフローを開始するために、のパブリックAPIを使用します。一方、インターフェイスは、ア `EntitlementMangerListener` プリケーションがイベントを処理するためのコールバックメカニズムを提 `EntitlementManger` 供します。

### EntitlementMangerコールバック

参照実装のメインアクティビティであ `CatalogActivity`る「」は、のインスタンスを `EntitlementManagerListener` 作成し、に登録します `EntitlementManager`。 この方法で、残りのアプリケ `EntitlementManager` ーションに対してUIの更新が必要な場合があります。 コールバックには、読み込み中のダイアログの表示/非表示、ステータスダイアログの表示、認証および認証アイコンの更新、認証が成功した場合のビデオ再生の開始が含まれます。

### 権利付与ダイアログ

クラスは、 `EntitlementDialogFragment` クラスのコンストラクターに渡されたエンタイトルメントのステータスに基づいてダイアログメッセージを生成します。 このクラスは、認証の成功メッセージおよびすべてのエラーメッセージに使用されます。 は、エン `CatalogActivity` タイトルメントダイアログを表示します。このダイアログは、から特定のイベントを受け取るときに表示され `EntitlementManager`ます。 さらに、はインターフェイスを `CatalogActivity` 実装しま `EntitlementDialogListener` す。このインターフェイスには、ダイアログが閉じられたとき、またはユーザーがPrimetime認証サービスからログアウトしたときに通知するコールバックメソッドが含まれます。

### コンテンツプロバイダーの選択とログイン

Primetime認証での認証中に、2つの新しいアクティビティが追加さ `MvpdPickerActivity` れ、ユ `MvpdLoginActivity`ーザーがコンテンツプロバイダーを選択してログインできるようになりました。 これらのアクティビティは、両方ともを介して `CatalogActivity` 開始されま `EntitlementManager`す。 また、とは、結果をに返 `MvpdPickerActivity` し、そ `MvpdLoginActivity` の結果をに返すと `CatalogActivity` 共に、メソッドを上 `CatalogActivity` 書きする必要があ `Activity.onActivityResult` ります。

### サインインボタン

参照実装のメインアクティビティ( `CatalogActivity`)のアクションバーに、新しい「サインイン」ボタンが追加されました。 「Sign In」ボタンを使用すると、ユーザーはPrimetime認証で認証を開始できます。 また、ユーザは、再生用の保護されたビデオを選択することで、認証を開始できます。 ログインボタンのアイコンとテキストは、ユーザーの認証ステータスに応じて変わります。には、ページが更新されたときにボタンのアイコンとテキストを更新するコードが含まれています。 `CatalogActivity` これを行うには、が起動すると、ユ `CatalogActivity` ーザーの認証ス `EntitlementManager.checkAuthentication()` テータスを更新するように呼び出します。

### コンテンツの権利付与

内の新し `CatalogView`いアイコンは、コンテンツのアイコンの上に表示され、そのコンテンツに対するユーザの認証ステータスを知らせます。 例えば、ユーザーがビデオの視聴を事前に承認されている場合、緑色の円のアイコンがコンテンツの上に表示されます。 ただし、ユーザーがビデオを表示する権限を事前に付与されていない場合は、キーアイコンが表示されます。 これらのアイコンの表示は、で処理さ `ContentTileAdapter`れますが、のコールバックが呼び出され `CatalogActivity` た時点から状態の更新が開始 `EntitlementManagerListener` されます。

### コンテンツの再生

ビデオ再生には、による認証チェックが必要になりまし `EntitlementManager`た。 呼び出しは、内で `EntitlementManager.getAuthorization()` 発生しま `CatalogView`す。 ビデオに認証が必要で、ユーザーが認証済みの場合は、 `PlayerActivity` から開始されま `CatalogActivity`す。


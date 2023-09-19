---
title: DRMManager クラスの使用：概要
description: DRMManager クラスの使用：概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# DRMManager クラスの使用 {#using-the-drmmanager-class}

以下を使用します。 `DRMManager` アプリケーション内のライセンスと Primetime DRM ライセンスサーバーセッションを管理するためのクラス。

**ライセンス管理**

デバイスが保護されたコンテンツを再生するたびに、ランタイムはコンテンツの表示に必要なライセンスを取得してキャッシュします。 アプリケーションがコンテンツをローカルに保存し、ライセンスがオフラインでの再生を許可している場合、ユーザーはネットワークに接続しなくても、アプリケーションのコンテンツを表示できます。 の使用 `DRMManager`を使用すると、ライセンスを事前にキャッシュできます。 コンテンツを表示するために必要なライセンスをアプリケーションが取得する必要はありません。 例えば、アプリケーションでメディアファイルをダウンロードし、ユーザーがオンラインの状態でライセンスを取得するとします。

ライセンスをプリロードするには、 `DRMContentData` オブジェクト。 The `DRMContentData` オブジェクトには、ライセンスを提供できる Primetime DRM ライセンスサーバーの URL が含まれます。この URL は、ユーザー認証が必要かどうかを示します。 この情報を使用して、 `DRMManager` `loadVoucher()` メソッドを使用して、ライセンスを取得およびキャッシュします。 プリロードライセンスのワークフローについて詳しくは、 *オフライン再生用のライセンスのプリロード*.

**セッション管理**

また、 `DRMManager` を使用して、Primetime DRM ライセンスサーバーに対するユーザーの認証を行い、永続セッションを管理します。 を呼び出します。 `DRMManager` `authenticate()` メソッドを使用して、Primetime DRM ライセンスサーバーとのセッションを確立します。 認証が正常に完了すると、 `DRMManager` を派遣する `DRMAuthenticationCompleteEvent` オブジェクト。 このオブジェクトにはセッショントークンが含まれています。 このトークンを保存して今後のセッションを確立し、ユーザーが自分のアカウントの資格情報を提供する必要がないようにすることができます。 トークンをに渡す `setAuthenticationToken()` メソッドを使用して、新しい認証済みセッションを確立します。 （トークンを生成したサーバーの設定によって、トークンの有効期限と他の属性が決まります）。

## DRMStatus イベントの処理 {#handling-drmstatus-events}

The `DRMManager` を派遣する `DRMStatusEvent` オブジェクトの後に `loadVoucher()` メソッドが正常に完了しました。 ライセンスが取得されると、イベントオブジェクトの detail プロパティに次の値が設定されます。 `DRM.voucherObtained`、および voucher プロパティには、 `DRMVoucher` オブジェクト。 ライセンスが取得されない場合、detail プロパティには次の値が設定されます。 `DRM.voucherObtained`ただし、voucher プロパティは null です。 例えば、 `LoadVoucherSetting` / `localOnly` ローカルにキャッシュされたライセンスはありません。 次の場合、 `loadVoucher()` 認証または通信エラーが原因で、呼び出しが正常に完了しなかった場合、 `DRMManager` を派遣する `DRMErrorEvent` または `DRMAuthenticationErrorEvent` オブジェクトを使用します。

## DRMAuthenticationComplete イベントの処理{#handling-drmauthenticationcomplete-events}

The `DRMManager` を派遣する `DRMAuthenticationCompleteEvent` オブジェクトを返します。 `authenticate()` メソッド。 The `DRMAuthenticationCompleteEvent` オブジェクトには、アプリケーションセッション間でユーザー認証を保持するために使用できる再利用可能なトークンが含まれています。 このトークンをに渡す `DRMManager` `setAuthenticationToken()` メソッドを使用して、セッションを再確立します。 ( トークンの作成者は、有効期限などのトークン属性を設定します。 Adobeは、トークンの属性を調べるための API を提供していません )。

## DRMAuthenticationError イベントの処理{#handling-drmauthenticationerror-events}

The `DRMManager` を派遣する `DRMAuthenticationErrorEvent` オブジェクトを返します。 `authenticate()` または `setAuthenticationToken()` メソッド。

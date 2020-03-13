---
seo-title: DRMManagerクラスの使用の概要
title: DRMManagerクラスの使用の概要
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# DRMManagerクラスの使用 {#using-the-drmmanager-class}

このクラスを使 `DRMManager` 用して、アプリケーションのライセンスとPrimetime DRMライセンスサーバーセッションを管理します。

**ライセンス管理**

保護されたコンテンツをデバイスが再生すると、ランタイムはコンテンツの表示に必要なライセンスを取得し、キャッシュします。 アプリケーションがコンテンツをローカルに保存し、ライセンスがオフラインでの再生を許可している場合、ユーザーはネットワークに接続しなくても、アプリケーション内のコンテンツを表示できます。 を使用して、ラ `DRMManager`イセンスを事前にキャッシュできます。 コンテンツを表示するために必要なライセンスを取得する必要はありません。 例えば、アプリケーションでメディアファイルをダウンロードし、ユーザーがオンラインの間、ライセンスを取得することができます。

ライセンスを事前に読み込むには、オブジェクトを使 `DRMContentData` 用します。 このオ `DRMContentData` ブジェクトには、ライセンスを提供できるPrimetime DRMライセンスサーバーのURLが含まれ、ユーザー認証が必要かどうかを示します。 この情報を使用して、このメソッドを呼び出し、 `DRMManager``loadVoucher()` ライセンスを取得してキャッシュできます。 ライセンスのプリロードのワークフローについては、オフライン再生用のプリロ *ードライセンスで詳しく説明しています*。

**セッション管理**

また、を使用して、Primetime DRMライ `DRMManager` センスサーバーに対するユーザーの認証や、永続的なセッションの管理を行うこともできます。 メソッドを呼 `DRMManager` び出し `authenticate()` て、Primetime DRMライセンスサーバーとのセッションを確立します。 認証が正常に完了すると、オブジェクト `DRMManager` がディスパッチ `DRMAuthenticationCompleteEvent` されます。 このオブジェクトには、セッショントークンが含まれます。 このトークンを保存して以降のセッションを確立し、ユーザーがアカウントの資格情報を提供する必要がないようにすることができます。 メソッドにトークンを渡し `setAuthenticationToken()` て、新しい認証済みセッションを確立します。 （トークンを生成したサーバーの設定によって、トークンの有効期限と他の属性が決まります）。

## DRMStatusイベントの処理 {#handling-drmstatus-events}

メソッド `DRMManager` の呼び出し `DRMStatusEvent` が正常に完了した後、オブジェク `loadVoucher()` トがディスパッチされます。 ライセンスを取得した場合、イベントオブジェクトのdetailプロパティの値は次のとおりです。voucherプロ `DRM.voucherObtained`パティにはオブジェクトが含ま `DRMVoucher` れます。 ライセンスが取得されない場合、detailプロパティの値は次のとおりです。 `DRM.voucherObtained`;ただし、voucherプロパティはnullです。 例えば、のを使用し、ローカルにキャッシュされたライセンスがな `LoadVoucherSetting` い場合、 `localOnly` ライセンスを取得できません。 認証または通 `loadVoucher()` 信エラーが原因で呼び出しが正常に完了しなかった場合は、代わりにまたはオ `DRMManager` ブジェクト `DRMErrorEvent` がディスパッ `DRMAuthenticationErrorEvent` チされます。

## DRMAuthenticationCompleteイベントの処理{#handling-drmauthenticationcomplete-events}

メソッ `DRMManager` ドの呼び出 `DRMAuthenticationCompleteEvent` しによってユーザーが正常に認証されると、オブジェクトがディスパッチさ `authenticate()` れます。 このオブジ `DRMAuthenticationCompleteEvent` ェクトには、アプリケーションセッション間でのユーザー認証を保持するために使用できる、再利用可能なトークンが含まれています。 このトークンをメソッドに渡 `DRMManager` して、 `setAuthenticationToken()` セッションを再確立します。 (トークンクリエーターは、有効期限などのトークン属性を設定します。 アドビでは、トークン属性を調べるAPIを提供していません。)

## DRMAuthenticationErrorイベントの処理{#handling-drmauthenticationerror-events}

またはメ `DRMManager` ソッドの呼び出 `DRMAuthenticationErrorEvent` しによってユーザーが正常に認証されなかった場合に、オブジェクト `authenticate()` がディスパッチさ `setAuthenticationToken()` れます。
---
seo-title: DRMManagerクラスの使用の概要
title: DRMManagerクラスの使用の概要
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# DRMManagerクラス{#using-the-drmmanager-class}の使用

`DRMManager`クラスを使用して、アプリケーション内のライセンスとPrimetime DRMライセンスサーバーセッションを管理します。

**ライセンス管理**

デバイスが保護されたコンテンツを再生するたびに、ランタイムはコンテンツの表示に必要なライセンスを取得してキャッシュします。 アプリケーションがコンテンツをローカルに保存し、ライセンスがオフライン再生を許可している場合、ユーザーはネットワークに接続せずにアプリケーション内のコンテンツを表示できます。 `DRMManager`を使用して、ライセンスを事前にキャッシュできます。 コンテンツの表示に必要なライセンスを取得する必要はありません。 例えば、アプリケーションでメディアファイルをダウンロードし、ユーザーがオンラインの間はライセンスを取得できます。

ライセンスを事前に読み込むには、`DRMContentData`オブジェクトを使用します。 `DRMContentData`オブジェクトには、ライセンスを提供できるPrimetime DRMライセンスサーバーのURLが含まれ、ユーザー認証が必要かどうかを示します。 この情報を使用して、`DRMManager` `loadVoucher()`メソッドを呼び出し、ライセンスを取得してキャッシュできます。 プリロードライセンスのワークフローについては、*オフライン再生用のプリロードライセンス*&#x200B;で詳しく説明されています。

**セッション管理**

`DRMManager`を使用して、Primetime DRMライセンスサーバーに対するユーザーの認証や、永続的なセッションの管理を行うこともできます。 `DRMManager` `authenticate()`メソッドを呼び出して、Primetime DRMライセンスサーバーとのセッションを確立します。 認証が正常に完了すると、`DRMManager`は`DRMAuthenticationCompleteEvent`オブジェクトをディスパッチします。 このオブジェクトには、セッショントークンが含まれます。 このトークンを保存して以降のセッションを確立し、ユーザーがアカウントの資格情報を提供する必要がないようにすることができます。 `setAuthenticationToken()`メソッドにトークンを渡して、新しい認証済みセッションを確立します。 （トークンを生成したサーバーの設定によって、トークンの有効期限やその他の属性が決まります）。

## DRMStatusイベントの処理{#handling-drmstatus-events}

`DRMManager`は、`loadVoucher()`メソッドの呼び出しが正常に完了した後、`DRMStatusEvent`オブジェクトをディスパッチします。 ライセンスを取得した場合、イベントオブジェクトのdetailプロパティに次の値が設定されます。`DRM.voucherObtained`、voucherプロパティには`DRMVoucher`オブジェクトが含まれます。 ライセンスが取得されない場合、detailプロパティの値は次のとおりです。`DRM.voucherObtained`;ただし、voucherプロパティはnullです。 例えば、`localOnly`の`LoadVoucherSetting`を使用していて、ローカルにキャッシュされたライセンスがない場合、ライセンスを取得できません。 `loadVoucher()`の呼び出しが正常に完了しない場合（認証または通信エラーが原因の場合など）、`DRMManager`は代わりに`DRMErrorEvent`または`DRMAuthenticationErrorEvent`オブジェクトをディスパッチします。

## DRMAuthenticationCompleteイベント{#handling-drmauthenticationcomplete-events}の処理

`DRMManager`は、ユーザーが`authenticate()`メソッドの呼び出しによって認証されると、`DRMAuthenticationCompleteEvent`オブジェクトをディスパッチします。 `DRMAuthenticationCompleteEvent`オブジェクトには、再利用可能なトークンが含まれており、これを使用してアプリケーションセッション間でユーザー認証を保持できます。 このトークンを`DRMManager` `setAuthenticationToken()`メソッドに渡して、セッションを再確立します。 (トークン作成者は有効期限などのトークン属性を設定します。 Adobeは、トークン属性を調べるAPIを提供しません。)

## DRMAuthenticationErrorイベント{#handling-drmauthenticationerror-events}の処理

`DRMManager`は、`authenticate()`メソッドまたは`setAuthenticationToken()`メソッドの呼び出しでユーザーが認証に成功しなかった場合に、`DRMAuthenticationErrorEvent`オブジェクトをディスパッチします。
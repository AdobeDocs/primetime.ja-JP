---
description: 通常、Primetime DRM ライセンスは作成時にはすべて一意のデバイスに結び付けられます。 このバインディングにより、ユーザーは認証を受けずに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRM は、デバイスごとのバインディングに加えて、ライセンスをデバイスドメイン（デバイスのグループ）にバインドする機能を提供します。
title: ドメインサポートを使用した暗号化コンテンツの再生
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# デバイスドメインのサポート {#device-domain-support}

通常、Primetime DRM ライセンスは作成時にはすべて一意のデバイスに結び付けられます。 このバインディングにより、ユーザーは認証を受けずに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRM は、デバイスごとのバインディングに加えて、ライセンスをデバイスドメイン（デバイスのグループ）にバインドする機能を提供します。

コンテンツメタデータでデバイスドメインの登録が必要と指定されている場合、アプリケーションは API を呼び出してデバイスグループに参加できます。 このアクションは、トリガーサーバーに送信されるドメイン登録要求をドメインに登録します。 デバイスグループに対してライセンスが発行されると、そのライセンスをエクスポートして、そのデバイスグループに参加している他のデバイスと共有することができます。

その後、デバイスグループの情報は、 `DRMContentData` `VoucherAccessInfo` オブジェクト。このオブジェクトは、ライセンスを正常に取得して使用するために必要な情報を提示するために使用されます。

## ドメインサポートを使用した暗号化コンテンツの再生 {#play-encrypted-content-using-domain-support}

Primetime DRM を使用して暗号化されたコンテンツを再生するには、次の手順を実行します。

1. 使用 `VoucherAccessInfo.deviceGroup`、デバイスグループの登録が必要かどうかを確認します。
1. 認証が必要な場合：
   1. 以下を使用します。 `DeviceGroupInfo.authenticationMethod` property 認証が必要かどうかを調べます。
   1. 認証が必要な場合は、次の手順のいずれかを実行してユーザーを認証します。

      * ユーザーのユーザー名とパスワードを取得し、を呼び出す `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * キャッシュ/事前生成された認証トークンを取得し、を呼び出す `DRMManager.setAuthenticationToken()`.

   1. 起動 `DRMManager.addToDeviceGroup()`
1. 次のいずれかのタスクを実行して、コンテンツのライセンスを取得します。
   1. 以下を使用します。 `DRMManager.loadVoucher()` メソッド。
   1. 同じデバイスグループに登録されている別のデバイスからライセンスを取得し、 `DRMManager` から `DRMManager.storeVoucher()` メソッド。
1. 暗号化されたコンテンツを `Primetime.play()` メソッド。
コンテンツのライセンスをエクスポートするために、任意のデバイスで、 `DRMVoucher.toByteArray()` メソッドを使用して、Primetime DRM ライセンスサーバーからライセンスを取得した後で、 通常、コンテンツプロバイダーはデバイスグループ内のデバイスの数を制限します。 上限に達した場合は、 `DRMManager.removeFromDeviceGroup()` メソッドを使用して、現在のデバイスを登録する前に使用しないデバイスに接続します。

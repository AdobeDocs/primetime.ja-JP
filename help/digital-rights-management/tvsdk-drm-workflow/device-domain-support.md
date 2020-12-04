---
description: 通常、Primetime DRMライセンスは作成時にすべて一意のデバイスに結び付けられます。 このバインディングにより、ユーザーは認証なしに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRMには、デバイスごとのバインディングに加えて、デバイスドメインまたはデバイスのグループにライセンスをバインドする機能があります。
seo-description: 通常、Primetime DRMライセンスは作成時にすべて一意のデバイスに結び付けられます。 このバインディングにより、ユーザーは認証なしに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRMには、デバイスごとのバインディングに加えて、デバイスドメインまたはデバイスのグループにライセンスをバインドする機能があります。
seo-title: ドメインのサポートを使用した暗号化コンテンツの再生
title: ドメインのサポートを使用した暗号化コンテンツの再生
uuid: 8854cc0f-9bfc-4833-82d7-a3f46ac88e06
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# デバイスドメインのサポート{#device-domain-support}

通常、Primetime DRMライセンスは作成時にすべて一意のデバイスに結び付けられます。 このバインディングにより、ユーザーは認証なしに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRMには、デバイスごとのバインディングに加えて、デバイスドメインまたはデバイスのグループにライセンスをバインドする機能があります。

コンテンツのメタデータでデバイスドメインの登録が必要と指定されている場合、アプリケーションはAPIを呼び出してデバイスグループに参加できます。 この操作により、ドメイン登録要求がトリガーされ、ドメインサーバーに送信されます。 デバイスグループにライセンスが発行されると、そのライセンスをエクスポートし、デバイスグループに参加している他のデバイスと共有できます。

次に、デバイスグループ情報が`DRMContentData` `VoucherAccessInfo`オブジェクトで使用され、このオブジェクトは、ライセンスの取得と消費に必要な情報を示すために使用されます。

## ドメインサポート{#play-encrypted-content-using-domain-support}を使用して暗号化コンテンツを再生

Primetime DRMを使用して暗号化されたコンテンツを再生するには、次の手順を実行します。

1. `VoucherAccessInfo.deviceGroup`を使用して、デバイスグループの登録が必要かどうかを確認します。
1. 認証が必要な場合：
   1. `DeviceGroupInfo.authenticationMethod`プロパティを使用して、認証が必要かどうかを調べます。
   1. 認証が必要な場合は、次のいずれかの手順を実行してユーザーを認証します。

      * ユーザーのユーザー名とパスワードを取得し、`DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`を呼び出します。
      * キャッシュ/事前生成された認証トークンを取得し、`DRMManager.setAuthenticationToken()`を呼び出します。
   1. `DRMManager.addToDeviceGroup()`を起動
1. 次のいずれかのタスクを実行して、コンテンツのライセンスを取得します。
   1. `DRMManager.loadVoucher()`メソッドを使用します。
   1. 同じデバイスグループに登録されている別のデバイスからライセンスを取得し、`DRMManager.storeVoucher()`メソッドを介して` DRMManager`にライセンスを提供します。
1. `Primetime.play()`メソッドを使用して、暗号化されたコンテンツを再生します。
コンテンツ用のライセンスを書き出すには、Primetime DRMライセンスサーバーからライセンスを取得した後、任意のデバイスで`DRMVoucher.toByteArray()`メソッドを使用してライセンスの生バイトを提供できます。 通常、コンテンツプロバイダーはデバイスグループ内のデバイス数を制限します。 上限に達した場合は、現在のデバイスを登録する前に、未使用のデバイスで`DRMManager.removeFromDeviceGroup()`メソッドを呼び出す必要がある場合があります。
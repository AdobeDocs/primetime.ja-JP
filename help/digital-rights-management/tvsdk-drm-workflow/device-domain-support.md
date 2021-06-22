---
description: 通常、Primetime DRMライセンスは作成時にすべて、一意のデバイスに結び付けられます。 このバインディングにより、ユーザーが認証を受けずに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRMは、デバイスごとのバインディングに加えて、デバイスドメイン（デバイスのグループ）にライセンスをバインドする機能を提供します。
title: ドメインサポートを使用した暗号化コンテンツの再生
exl-id: 3c9badfc-046b-4c56-bde1-7b3b708bfaa2
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# デバイスドメインのサポート{#device-domain-support}

通常、Primetime DRMライセンスは作成時にすべて、一意のデバイスに結び付けられます。 このバインディングにより、ユーザーが認証を受けずに異なるデバイス間でライセンスを共有できなくなります。 Primetime DRMは、デバイスごとのバインディングに加えて、デバイスドメイン（デバイスのグループ）にライセンスをバインドする機能を提供します。

コンテンツメタデータがデバイスドメインの登録が必要であることを指定した場合、アプリケーションはAPIを呼び出してデバイスグループに参加できます。 このアクションは、トリガーサーバーに送信されるドメイン登録要求を設定します。 デバイスグループに対してライセンスが発行されると、そのライセンスをエクスポートし、そのデバイスグループに参加している他のデバイスと共有できます。

次に、デバイスグループ情報を`DRMContentData` `VoucherAccessInfo`オブジェクトで使用し、この情報を使用して、ライセンスを正常に取得して使用するために必要な情報を表示します。

## ドメインサポート{#play-encrypted-content-using-domain-support}を使用した暗号化コンテンツの再生

Primetime DRMを使用して暗号化されたコンテンツを再生するには、次の手順を実行します。

1. `VoucherAccessInfo.deviceGroup`を使用して、デバイスグループの登録が必要かどうかを確認します。
1. 認証が必要な場合：
   1. `DeviceGroupInfo.authenticationMethod`プロパティを使用して、認証が必要かどうかを調べます。
   1. 認証が必要な場合は、次の手順のいずれかを実行してユーザーを認証します。

      * ユーザーのユーザー名とパスワードを取得し、`DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`を呼び出します。
      * キャッシュまたは事前生成された認証トークンを取得し、`DRMManager.setAuthenticationToken()`を呼び出します。
   1. `DRMManager.addToDeviceGroup()`を呼び出す
1. 次のいずれかのタスクを実行して、コンテンツのライセンスを取得します。
   1. `DRMManager.loadVoucher()`メソッドを使用します。
   1. 同じデバイスグループに登録されている別のデバイスからライセンスを取得し、`DRMManager.storeVoucher()`メソッドを通じて`DRMManager`にライセンスを提供します。
1. `Primetime.play()`メソッドを使用して、暗号化されたコンテンツを再生します。
コンテンツ用のライセンスを書き出すために、任意のデバイスは、Primetime DRMライセンスサーバーからライセンスを取得した後、`DRMVoucher.toByteArray()`メソッドを使用してライセンスの生のバイトを提供できます。 通常、コンテンツプロバイダーはデバイスグループ内のデバイス数を制限します。 制限に達した場合は、現在のデバイスを登録する前に、未使用のデバイスで`DRMManager.removeFromDeviceGroup()`メソッドを呼び出す必要がある場合があります。

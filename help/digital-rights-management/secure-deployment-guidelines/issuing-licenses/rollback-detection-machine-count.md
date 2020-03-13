---
description: ビジネスルールでユーザーのマシン数を追跡する必要がある場合、ライセンスサーバーまたはドメインサーバーには、そのユーザーに関連付けられたマシンIDを格納する必要があります。
seo-description: ビジネスルールでユーザーのマシン数を追跡する必要がある場合、ライセンスサーバーまたはドメインサーバーには、そのユーザーに関連付けられたマシンIDを格納する必要があります。
seo-title: ライセンス発行時のコンピューター数
title: ライセンス発行時のコンピューター数
uuid: 7ba8a8d4-a31f-4f37-82a7-755cfa443544
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# ライセンス発行時のコンピューター数 {#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、ライセンスサーバーまたはドメインサーバーには、そのユーザーに関連付けられたマシンIDを格納する必要があります。

マシンIDを追跡する最も強力な方法は、 [MachineId.getBytes()メソッドによって返される値をデータベースに格納することです](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) 。 新しい要求を受け取った場合、MachineId.matches()を使用して、要求内のマシンIDと既知のマシンID [を比較します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId))。

[MachineId.matches()は](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) 、IDの比較を実行して、IDが同じマシンを表しているかどうかを判断します。 この比較は、マシンIDの数が少ない場合にのみ実用的です。 例えば、ユーザーがドメイン内で5台のマシンを使用できる場合は、データベースでそのユーザーのユーザー名に関連付けられているマシンIDを検索し、比較用の小さなデータセットを取得できます。

この比較は、匿名アクセスを許可するデプロイメントでは実用的ではありません。 この場合、 [MachineId.getUniqueID()を使用できます](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) 。 ただし、ユーザーがFlashおよびAdobe AIR®ランタイムからコンテンツにアクセスした場合、このIDは同じにできません。

>[!NOTE]
>
>IDは、ユーザーがハードドライブを再フォーマットした場合には保持されません。
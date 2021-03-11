---
description: ビジネスルールでユーザーのマシン数を追跡する必要がある場合、License Serverまたはドメインサーバーには、ユーザーに関連付けられたマシンIDを格納する必要があります。
title: ライセンス発行時のコンピュータ数
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# ライセンス発行時のマシン数{#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、License Serverまたはドメインサーバーには、ユーザーに関連付けられたマシンIDを格納する必要があります。

マシンIDを追跡する最も強力な方法は、データベース内の[MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes())メソッドから返された値を格納することです。 新しい要求を受け取ったら、[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId))を使用して、要求内のマシンIDと既知のマシンIDを比較します。

[MachineId.matches()は、IDの比較を](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) 実行して、IDが同じマシンを表しているかどうかを判断します。この比較は、マシンIDの数が少ない場合にのみ実用的です。 例えば、ドメインに5台のマシンを許可されている場合、データベースでそのユーザーのユーザー名に関連付けられているマシンIDを検索し、比較用に小さなデータセットを取得できます。

この比較は、匿名アクセスを許可するデプロイメントでは実用的ではありません。 この場合、[MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())を使用できます。 ただし、ユーザーがFlashおよびAdobe AIR®ランタイムからコンテンツにアクセスする場合、このIDを同じにすることはできません。

>[!NOTE]
>
>IDは、ユーザーがハードドライブの形式を変更した場合には保持されません。
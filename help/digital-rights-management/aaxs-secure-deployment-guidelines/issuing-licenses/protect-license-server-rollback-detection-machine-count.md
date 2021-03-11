---
title: ライセンス発行時のコンピュータ数
description: ライセンス発行時のコンピュータ数
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# ライセンス発行時のマシン数{#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、License Serverまたはドメインサーバーには、ユーザーに関連付けられたマシンIDを格納する必要があります。 マシンIDを追跡する最も強力な方法は、`MachineId.getBytes()`メソッドから返された値をデータベースに格納することです。 新しい要求が入ってきたら、`MachineId.matches()`を使用して、要求内のマシンIDと既知のマシンIDを比較します。

`MachineId.matches()` は、IDの比較を実行して、同じマシンを表しているかどうかを判断します。この比較は、比較対象のマシンIDが少数ある場合にのみ実用的です。 例えば、ユーザーがドメイン内で5台のマシンを許可されている場合、データベースでそのユーザーのユーザー名に関連付けられたマシンIDを検索し、比較対象となる小さなデータセットを取得できます。

>[!NOTE]
>
>この比較は、匿名アクセスを許可する展開では実用的ではありません。 このような場合は`MachineId.getUniqueID()`を使用できますが、FlashとAdobe AIR®ランタイムの両方からコンテンツにアクセスした場合、このIDは同じではなく、ユーザーがハードドライブを再フォーマットした場合、このIDは使用できません。

`MachineToken.getMachineId()`と`MachineId.matches()`について詳しくは、*AdobeアクセスAPIリファレンス*&#x200B;を参照してください。

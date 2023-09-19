---
title: ライセンス発行時のコンピューター数
description: ライセンス発行時のコンピューター数
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# ライセンス発行時のコンピューター数{#machine-count-when-issuing-licenses}

ビジネス・ルールでユーザーのマシン数を追跡する必要がある場合は、ライセンス・サーバーまたはドメイン・サーバーにユーザーに関連付けられたマシン ID を保存する必要があります。 マシン ID を追跡する最も堅牢な方法は、 `MachineId.getBytes()` メソッドを使用して、データベース内で設定できます。 新しいリクエストが発生したら、を使用して、リクエスト内のマシン ID と既知のマシン ID を比較します。 `MachineId.matches()`.

`MachineId.matches()` は、ID の比較を実行して、同じマシンを表しているかどうかを判断します。 この比較は、比較対象のマシン ID が少数ある場合にのみ実用的です。 例えば、ユーザーがドメイン内で 5 台のマシンを許可されている場合は、データベースでユーザー名に関連付けられているマシン ID を検索し、比較対象となる小さなデータセットを取得できます。

>[!NOTE]
>
>この比較は、匿名アクセスを許可するデプロイメントには実用的ではありません。 このような場合 `MachineId.getUniqueID()` ただし、FlashとAdobe AIR®のランタイムの両方からコンテンツにアクセスする場合は、この ID が同じではなくなり、ユーザーがハードドライブを再フォーマットした場合は存続しません。

詳しくは、以下を参照してください。 `MachineToken.getMachineId()`および `MachineId.matches()`を参照し、 *Adobeアクセス API リファレンス*.

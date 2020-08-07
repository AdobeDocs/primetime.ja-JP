---
seo-title: ライセンス発行時のコンピュータ数
title: ライセンス発行時のコンピュータ数
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# ライセンス発行時のコンピュータ数{#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、License Serverまたはドメインサーバーには、ユーザーに関連付けられたマシンIDを格納する必要があります。 マシンIDを追跡する最も堅牢な方法は、 `MachineId.getBytes()` メソッドから返された値をデータベースに格納することです。 新しい要求が入ってきたら、を使用して、要求内のマシンIDと既知のマシンIDを比較し `MachineId.matches()`ます。

`MachineId.matches()` は、IDの比較を実行して、同じマシンを表しているかどうかを判断します。 この比較は、比較対象のマシンIDが少数ある場合にのみ実用的です。 例えば、ユーザーがドメイン内で5台のマシンを許可されている場合、データベースでそのユーザーのユーザー名に関連付けられているマシンIDを検索し、比較対象となる小さなデータセットを取得できます。

>[!NOTE]
>
>この比較は、匿名アクセスを許可する展開では実用的ではありません。 ただし、このような場合 `MachineId.getUniqueID()` は、FlashとAdobe AIR®ランタイムの両方からコンテンツにアクセスした場合、このIDは同じではなく、ユーザーがハードドライブを再フォーマットした場合、このIDは維持されません。

お `MachineToken.getMachineId()`よびについて詳しくは、 `MachineId.matches()`AdobeアクセスAPIリファレンスを参照してください **。

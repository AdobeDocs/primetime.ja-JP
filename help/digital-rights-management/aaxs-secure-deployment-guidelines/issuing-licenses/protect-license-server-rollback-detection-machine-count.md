---
seo-title: ライセンス発行時のコンピューター数
title: ライセンス発行時のコンピューター数
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# ライセンス発行時のコンピューター数{#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合は、License Serverまたはドメインサーバーに、そのユーザーに関連付けられたマシンIDを保存する必要があります。 マシンIDを追跡する最も堅牢な方法は、メソッドが返す値をデータベースに格納 `MachineId.getBytes()` することです。 新しい要求が入ったら、要求内のマシンIDと、を使用して既知のマシンIDとを比較しま `MachineId.matches()`す。

`MachineId.matches()` は、IDの比較を実行して、同じマシンを表しているかどうかを判断します。 この比較は、比較対象のマシンIDの数が少ない場合にのみ実用的です。 例えば、ユーザーがドメイン内で5台のマシンを使用できる場合は、データベース内でユーザーのユーザー名に関連付けられたマシンIDを検索し、比較対象の小さなデータセットを取得できます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この比較は、匿名アクセスを許可するデプロイメントでは実用的ではありません。 ただし、この場 `MachineId.getUniqueID()` 合、ユーザーがFlashとAdobe AIR®の両方のランタイムからコンテンツにアクセスした場合、このIDは同じではなく、ユーザーがハードドライブを再フォーマットした場合も、このIDは維持されません。

およびについて詳しく `MachineToken.getMachineId()`は、 `MachineId.matches()`『 *Adobe Access API Reference』を参照してください*。

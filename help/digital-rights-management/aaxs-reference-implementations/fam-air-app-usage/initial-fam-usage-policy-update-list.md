---
title: ポリシー更新リスト
description: ポリシー更新リスト
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# ポリシー更新リスト {#policy-update-list}

ポリシー更新リストを使用して、ポリシーの変更をライセンスサーバーに伝えることができます。 コンテンツのパッケージ化に使用した後にポリシーを変更した場合は、License Server にポリシーの最新バージョンを認識させ、バージョンを使用してライセンスを発行できるようにすることをお勧めします。

ポリシー更新リストを初めて作成する場合は、 **[!UICONTROL Add policies]** ：サーバー上の使用可能なすべてのポリシーを表示します。 コンテンツのパッケージ化に使用されてから更新されたポリシーに対して、 **[!UICONTROL update]** ラジオボタン。

ポリシーを使用してライセンスを発行したくなくなり、そのポリシーが既にコンテンツのパッケージ化に使用されている場合は、ポリシーを失効させることができます。 これをおこなうには、「 **[!UICONTROL revoke]** ラジオボタン。 目的のポリシーを選択したら、「 」を選択します。 **[!UICONTROL Create Policy Update List]**. というファイル [!DNL PolicyUpdateList.dat] が [!DNL Resources] ディレクトリ。

既存のポリシー更新リストを変更するには、 **[!UICONTROL Add policies]** ：サーバー上の使用可能なすべてのポリシーを表示します。 追加または取り消す追加のポリシーを選択します。 画面の上部のセクションで、ポリシー更新リストの既存のエントリを変更できます。 マークされたポリシー **[!UICONTROL updated]** は次のように変更される場合があります。 **[!UICONTROL revoked]**&#x200B;ただし、ポリシーが **[!UICONTROL revoked]**&#x200B;の場合、次の値に戻すことはできません： **[!UICONTROL updated]**.

必要な変更が加えられたら、 **[!UICONTROL Create Policy Update List]**、および [!DNL PolicyUpdateList.dat] ファイルが再生成されます。 ポリシーが既にポリシー更新リストに存在し、リストが最後に生成された時点以降に更新された場合は、ポリシー更新リストが再生成されたときに、最新バージョンのポリシーが使用されます。

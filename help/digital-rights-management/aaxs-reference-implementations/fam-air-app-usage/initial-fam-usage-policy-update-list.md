---
seo-title: ポリシーの更新リスト
title: ポリシーの更新リスト
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ポリシーの更新リスト {#policy-update-list}

ポリシー更新リストを使用して、ポリシーの変更をライセンスサーバーに通知できます。 ポリシーをコンテンツのパッケージ化に使用した後に変更する場合は、License Serverにポリシーの最新バージョンを認識させて、バージョンを使用してライセンスを発行できるようにすることが望ましいです。

初めてポリシー更新リストを作成するには、をクリックして、サーバー上 **[!UICONTROL Add policies]** で使用可能なすべてのポリシーを表示します。 コンテンツのパッケージ化に使用されてから更新されたポリシーの場合は、ラジオボタンを **[!UICONTROL update]** 選択します。

ポリシーを使用してライセンスを発行したくなくなり、そのポリシーが既にコンテンツのパッケージ化に使用されている場合は、ポリシーを無効にすることができます。 これを行うには、ラジオボタンを **[!UICONTROL revoke]** 選択します。 目的のポリシーを選択したら、を選択しま **[!UICONTROL Create Policy Update List]**&#x200B;す。 というファイルが [!DNL PolicyUpdateList.dat] ディレクトリに保存さ [!DNL Resources] れます。

既存のポリシー更新リストを変更するには、をクリックし **[!UICONTROL Add policies]** て、サーバー上で使用可能なすべてのポリシーを表示します。 追加または取り消す追加のポリシーを選択します。 画面の上部のセクションで、「Policy Update List」の既存のエントリを変更できます。 マークされたポリシ **[!UICONTROL updated]** ーはに変更でき **[!UICONTROL revoked]**&#x200B;ますが、ポリシーが一旦変更さ **[!UICONTROL revoked]**&#x200B;れると、に戻すことはできませ **[!UICONTROL updated]**&#x200B;ん。

必要な変更が行われたら、を選択し、フ **[!UICONTROL Create Policy Update List]**&#x200B;ァイルを再 [!DNL PolicyUpdateList.dat] 生成します。 ポリシーが既にポリシー更新リストに含まれ、リストの最後の生成時から更新されている場合は、ポリシー更新リストが再び生成される際に、ポリシーの最新バージョンが使用されます。

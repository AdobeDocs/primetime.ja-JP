---
title: ポリシーの更新リスト
description: ポリシーの更新リスト
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# ポリシー更新リスト{#policy-update-list}

ポリシーの更新リストを使用して、ポリシーの変更をLicense Serverに伝えることができます。 ポリシーをコンテンツのパッケージ化に使用した後に変更する場合は、License Serverにポリシーの最新バージョンを認識させて、ライセンスの発行に使用できるようにすることが望ましいです。

Policy Updateリストを初めて作成する場合は、**[!UICONTROL Add policies]**&#x200B;をクリックして、サーバー上で使用可能なすべてのポリシーを表示します。 コンテンツのパッケージ化に使用された後に更新されたポリシーに対しては、**[!UICONTROL update]**&#x200B;ラジオボタンを選択します。

ライセンスの発行にポリシーを使用しなくなり、そのポリシーが既にコンテンツのパッケージ化に使用されている場合は、ポリシーを無効にすることができます。 これを行うには、**[!UICONTROL revoke]**&#x200B;ラジオボタンを選択します。 目的のポリシーを選択したら、**[!UICONTROL Create Policy Update List]**&#x200B;を選択します。 [!DNL PolicyUpdateList.dat]というファイルが[!DNL Resources]ディレクトリに保存されます。

既存のポリシー更新リストを変更するには、**[!UICONTROL Add policies]**&#x200B;をクリックして、サーバー上の使用可能なすべてのポリシーを表示します。 追加または取り消す追加のポリシーを選択します。 「Policy Update」リストの既存のエントリは、画面の上部セクションで変更できます。 **[!UICONTROL updated]**&#x200B;とマークされたポリシーは&#x200B;**[!UICONTROL revoked]**&#x200B;に変更できますが、ポリシーが&#x200B;**[!UICONTROL revoked]**&#x200B;になると、**[!UICONTROL updated]**&#x200B;に戻すことはできません。

必要な変更が行われたら、**[!UICONTROL Create Policy Update List]**&#x200B;を選択し、[!DNL PolicyUpdateList.dat]ファイルを再生成します。 ポリシーが既にポリシー更新リストにあり、前回のリスト生成以降に更新された場合は、ポリシー更新リストが再生成される際に、最新のバージョンのポリシーが使用されます。

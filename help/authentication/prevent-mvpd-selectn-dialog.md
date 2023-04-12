---
title: 選択ダイアログに MVPD が表示されないようにする
description: 選択ダイアログに MVPD が表示されないようにする
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# 選択ダイアログに MVPD が表示されないようにする

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## 問題 {#issue-prevent-mvpd-sel-dialog}

(「block-list」) 特定の MVPD が MVPD セレクターに表示されないようにする必要があります。


## 解決策 {#solution-prevent-mvpd-sel-dialog}

解決策は、次の場合にブロックリストを作成することです。 `displayProviderDialog()` が呼び出されます。

例えば、CableCompany_1 と CableCompany_2 を MVPD セレクター内に表示しないようにする場合は、次の例に示すような処理を行います。

```C
function displayProviderDialog(mvpdList) {
    var allowlisted = new Array();
    for (var i = 0; i < mvpdList.length; i = i + 1) {
        var currentMvpd = mvpdList[i];
        if (!isBlocklisted(currentMvpd.ID)) {
            allowlisted.push(currentMvpd);
        }
    }
    displayAllowlisted(allowlisted);
}

function isBlocklisted(mvpdID) {
    // Implement block-listing on MVPD IDs.
    return (mvpdID === 'CableCompany_1' || mvpdID === 'CableCompany_2');
}

function displayAllowlisted(list) {
    // TODO: Implement site-specific logic here.
} 
```

<!--
**Related Information**

* [Allow MVPDs in the Selection Dialog](/help/authentication/allow-mvpd-selectn-dialog.md)
* **Code samples**
* [Programmer integration guide](/help/authentication/programmer-integration-guide-overview.md)
-->
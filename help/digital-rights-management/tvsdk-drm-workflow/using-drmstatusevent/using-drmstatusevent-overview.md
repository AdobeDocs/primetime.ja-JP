---
seo-title: DRMStatusEventクラスの使用の概要
title: DRMStatusEventクラスの使用の概要
uuid: 9faf35fe-63ac-43a8-a945-4735c12efb04
translation-type: tm+mt
source-git-commit: 9bbcb228d3367fbf53de811bf2941ca653ce3b0e
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# 概要{#using-the-drmstatusevent-class-overview}

Primetime DRMで保護されたコンテンツの再生が正常に開始されると、`DRMStatusEvent`オブジェクトがディスパッチされます。 (成功は、ライセンスが検証され、ユーザーが認証され、コンテンツの表示が許可されることを意味します)。

`DRMStatusEvent`オブジェクトには、ライセンスをオフラインで使用できるか、ライセンスの有効期限が切れた場合にコンテンツを表示できなくなるかなど、ライセンスに関する情報が含まれます。

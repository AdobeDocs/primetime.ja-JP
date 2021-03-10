---
title: DRMStatusEventクラスの使用の概要
description: DRMStatusEventクラスの使用の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# 概要{#using-the-drmstatusevent-class-overview}

Primetime DRMで保護されたコンテンツの再生が正常に開始されると、`DRMStatusEvent`オブジェクトがディスパッチされます。 (成功は、ライセンスが検証され、ユーザーが認証され、コンテンツの表示が許可されることを意味します)。

`DRMStatusEvent`オブジェクトには、ライセンスをオフラインで使用できるか、ライセンスの有効期限が切れた場合にコンテンツを表示できなくなるかなど、ライセンスに関する情報が含まれます。

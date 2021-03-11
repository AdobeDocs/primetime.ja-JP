---
description: DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限事項と要件を確認します。
title: コンテンツとマニフェストの要件
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---


# コンテンツとマニフェストの要件{#content-and-manifest-requirements}

DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限事項と要件を確認します。

| マニフェストファイル内の各ABRストリームに対して`RESOLUTION`プロパティを含め、設定します。 Flash Player14以降を使用する必要があります。 |
|---|
| DRM保護されたストリームがマルチビットレート(MBR)の場合、MBRで使用されるDRM暗号化キーは、すべてのビットレートストリームで使用されるキーと同じでなければなりません。 |
| メインコンテンツのレンディションと同じビットレートレンディションが必要です。 |
---
description: DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限事項と要件を確認します。
seo-description: DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限事項と要件を確認します。
seo-title: コンテンツとマニフェストの要件
title: コンテンツとマニフェストの要件
uuid: 53cc570a-be33-4488-95e8-43f91b559b13
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# コンテンツとマニフェストの要件{#content-and-manifest-requirements}

DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限事項と要件を確認します。

| マニフェストファイル内の各ABRストリームに対して`RESOLUTION`プロパティを含め、設定します。 Flash Player14以降を使用する必要があります。 |
|---|
| DRM保護されたストリームがマルチビットレート(MBR)の場合、MBRで使用されるDRM暗号化キーは、すべてのビットレートストリームで使用されるキーと同じでなければなりません。 |
| メインコンテンツのレンディションと同じビットレートレンディションが必要です。 |
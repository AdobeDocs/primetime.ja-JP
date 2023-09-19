---
description: DRM 暗号化キーを含む、ストリームと再生リスト（マニフェスト）の制限事項と要件を確認します。
title: コンテンツとマニフェストの要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# コンテンツとマニフェストの要件 {#content-and-manifest-requirements}

DRM 暗号化キーを含む、ストリームと再生リスト（マニフェスト）の制限事項と要件を確認します。

| を含め、 `RESOLUTION` プロパティは、マニフェストファイル内の各 ABR ストリームに対して設定されます。 Flash Player14 以降を使用する必要があります。 |
|---|
| DRM 保護されたストリームがマルチビットレート (MBR) の場合、MBR に使用される DRM 暗号化キーは、すべてのビットレートストリームで使用されるキーと同じである必要があります。 |
| メインコンテンツのレンディションと同じビットレートレンディションが必要です。 |

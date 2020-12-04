---
seo-title: 証明書の展開
title: 証明書の展開
uuid: adf72b51-be0f-49ec-83f7-152a378b04e6
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# 証明書を展開する{#deploy-certificates}

PFXパスワードがLicense Server上のクリアテキストで使用できないようにするには、リファレンスの実装と保護されたストリーミング用Adobe PrimetimeDRMサーバーで、設定ファイルで指定するパスワードを暗号化する必要があります。 スクランブリングユーティリティの実行手順については、「*Primetime DRM参照実装の使用*」または「*保護されたストリーミングにPrimetime DRMサーバー*&#x200B;を使用する」を参照してください。 それぞれには、独自のスクランブルユーティリティが含まれ、暗号化されたパスワードは、これらの2つのLicense Server実装間で交換できません。

証明書とスクランブルされたパスワードをライセンスサーバーにデプロイするには、*Primetime DRM参照実装の使用*&#x200B;または&#x200B;*保護ストリーミング用のPrimetime DRMサーバーの使用*&#x200B;を参照してください。

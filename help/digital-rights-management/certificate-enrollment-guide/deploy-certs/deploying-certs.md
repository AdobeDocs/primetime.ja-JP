---
seo-title: 証明書のデプロイ
title: 証明書のデプロイ
uuid: adf72b51-be0f-49ec-83f7-152a378b04e6
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# 証明書のデプロイ{#deploy-certificates}

PFXパスワードがLicense Server上のクリアテキストで使用されないようにするには、設定ファイルで指定したパスワードを、リファレンスの実装とAdobe Primetime DRM Serverで暗号化する必要があります。 スクラン *ブリングユーティリティの実行手順については、* Primetime DRM参照実装の使用 *（英語のみ）またはPrimetime DRM Server* for Protected Streamingの使用（英語のみ）を参照してください。 各スクランブルユーティリティには、それぞれ独自のスクランブルユーティリティが含まれ、暗号化されたパスワードは、これら2つのLicense Server実装間で交換できません。

証明書とスクランブルされたパスワードをライセンスサーバーにデプロイする方法については、 *Primetime DRM参照の実装の使用* （英語のみ）またはPrimetime DRMサー *バーを使用した保護されたストリーミング（英語のみ）を参照してください*。

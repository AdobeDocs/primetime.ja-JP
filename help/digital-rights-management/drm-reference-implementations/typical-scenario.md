---
description: 'null'
seo-description: 'null'
seo-title: 一般的なワークフロー
title: 一般的なワークフロー
uuid: aafe0030-8a59-4090-aeac-76867777eaa5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# 一般的なワークフロー{#typical-workflow}

次に示すのは、コマンドラインツールとライセンスサーバーの両方を備えた、一般的なPrimetime DRM参照実装ワークフローです。

1. ポリシーコマンドラインツールを使用してDRMポリシーを作成します。
1. Packagerのコマンドラインツールを使用して、コンテンツを暗号化します。
1. 参照実装のライセンスサーバーをデプロイします。
1. ビデオプレーヤーをWebサーバーにアップロードします。
1. アップロードしたビデオプレーヤーを使用して、ライセンスを取得し、暗号化されたコンテンツを再生します。

この一般的なワークフローでは、コマンドラインツールとライセンスサーバーの両方を使用するので、続行する前に、これらの両方のコンポーネントをインストールして設定する必要があります。

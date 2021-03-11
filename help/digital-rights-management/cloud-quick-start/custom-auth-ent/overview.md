---
title: ハチの概要
description: ハチの概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# ハチの概要{#bees-overview}

バックエンド権利付与サービス(BEES)を実装して、Primetime Cloud DRM操作のカスタム権利付与を提供できます。

Primetime Cloud DRMは、デフォルトで匿名ライセンス配信を使用します。 つまり、Primetime Cloud DRMに送信されるすべてのライセンス要求は、追加の認証/認証チェックを実行せずに有効なライセンスを返します(Adobe Primetime認証を呼び出すポリシー制約を適用していない場合)。

ライセンス要求には、コンテンツのパッケージ化/暗号化の際に使用されたDRMポリシーが含まれます。 DRMポリシーは、クライアントに返されたDRMライセンスの生成に使用されます。 デフォルトのシナリオでは、コンテンツのパッケージ化の際にすべてのDRMポリシーの決定を行う必要があります。 これらのワークフローをより細かく制御する必要がある場合は、次のオプションを使用できます。

1. Primetime認証を統合し、再生前に追加のエンタイトルメントチェックを追加します。
1. Primetime Cloud DRMがクエリしてから、パッケージ化したコンテンツの再生を任意のデバイスで許可するオンプレミスのエンタイトルメントサービスを作成します。

オンプレミスのエンタイトルメントサービスは、次の2つのデータを含むPrimetime Cloud DRMへの応答を提供する必要があります。

* `isAllowed`
* `drmPolicyToUse`

これらは、デバイスがコンテンツの再生を許可されるかどうか、およびDRMライセンスの生成に使用するDRMポリシーを決定します（`isAllowed`がtrueの場合）。

このドキュメントでは、上記のオプション2を実行するために必要な作業を説明します。独自のオンプレミス外部エンタイトルメントサービスを実装し、Primetime Cloud DRMでパッケージ化したコンテンツの利用を可能にします。

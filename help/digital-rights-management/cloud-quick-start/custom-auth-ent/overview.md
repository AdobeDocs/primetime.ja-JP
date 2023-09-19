---
title: 蜂の概要
description: 蜂の概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 蜂の概要{#bees-overview}

バックエンド使用権限サービス (BEES) を実装して、Primetime Cloud DRM 操作のカスタム使用権限を付与することができます。

Primetime Cloud DRM は、デフォルトで匿名のライセンス配信を使用します。 つまり、Primetime Cloud DRM に送信されたすべてのライセンスリクエストは、追加の認証/承認チェックを実行せずに有効なライセンスを返します (Adobe Primetime認証を使用するように要求するポリシー制約を適用している場合を除く )。

ライセンスリクエストには、コンテンツのパッケージ化/暗号化中に使用された DRM ポリシーが含まれます。 DRM ポリシーは、クライアントに返される DRM ライセンスの生成に使用されます。 デフォルトのシナリオでは、コンテンツのパッケージ化時にすべての DRM ポリシーの決定を行う必要があります。 これらのワークフローをより細かく制御するには、次のオプションを使用できます。

1. Primetime 認証を統合して、再生前に追加のエンタイトルメントチェックを追加します。
1. パッケージ化されたコンテンツの再生を任意のデバイスで許可する前に Primetime Cloud DRM がクエリするオンプレミスのエンタイトルメントサービスを作成します。

オンプレミスのエンタイトルメントサービスは、次の 2 つのデータを含む Primetime Cloud DRM への応答を提供する必要があります。

* `isAllowed`
* `drmPolicyToUse`

これらは、デバイスがコンテンツを再生できるかどうか、および DRM ライセンスの生成に使用する DRM ポリシー ( `isAllowed` が true の場合は除く )。

このドキュメントでは、上記の Option 2 の実行に必要な作業を説明します。独自のオンプレミス外部エンタイトルメントサービスを実装し、パッケージ化したコンテンツを Primetime Cloud DRM で利用できるようにします。

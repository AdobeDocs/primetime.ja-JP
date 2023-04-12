---
title: Adobe Primetime authentication 2.63 リリースノート
description: Adobe Primetime authentication 2.63 リリースノート
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Adobe Primetime Authentication 2.63 リリースノート {#pt-authn-263-rn}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

このページでは、このリリースの新機能、変更点および既知の問題について説明します。

## サーバー側および Web クライアント {#server-side-web-clients-263}

* [ビルド番号](#build-number)
* [新機能](#new-features)

### ビルド番号 {#build-number-263}

Adobe Primetime認証：adobe-pass-**2.63**
リリース日： **09/20/2022 - 09/22/2022**

### 新機能 {#new-features-263}

#### プラットフォームの識別メカニズムの改善 {#pf-identification-mech}

* このリリース以降、デバイスの識別に使用するメカニズムが改善され、クライアント側の実装に依存しなくなりました。 これにより、プラットフォームレベルでビジネスルールを適用する際の精度が向上し、ESM レポートのトラフィック値をより深く理解できます。

* 新しい ESM リリースは間もなく追加され、プラットフォーム関連のフィールドを公開する新しいレポートと改善されたレポートが追加されます。

* 計画された変更の詳細については、担当の TAM にお問い合わせください。

#### MVPD 自己分解 {#mvpd-self-degradation}

この機能は、MVPD に対して、それぞれのエンドポイントの負荷が大きくなりすぎた場合に、高トラフィックシナリオに対して独自の認証および承認エンドポイントを一時的にバイパスする機能を提供します。


#### 認証呼び出しのヘッダーにプロキシ化 ID を追加 {#add-proxied-id}

この機能は、認証呼び出しのヘッダーに Synacor プロキシ化された MVPD の ID を追加します。 これにより、Synacor は、個々のプロキシ ( プロキシ化された MVPD ごとに異なるドメインへのルーティング )。


#### TVE ダッシュボード {#tve-dashboard}

このリリースでは、MVPD レベルで設定された authN または authZ の TTL が設定レポートで正しく計算されなかった問題を修正しました。


#### JavaScript SDK 4.6.0 {#js-sdk}

* の使用を削除しました。 `eval` 関数を使用して、SDK をコンテンツセキュリティポリシーに準拠させることができます。
* ブラウザーのローカルストレージがパートナーアプリケーションによって明示的にクリアされた場合に、認証フローが正常に完了しない問題を修正しました。




---
title: Adobe Primetime authentication 2.64.1リリースノート
description: Adobe Primetime authentication 2.64.1リリースノート
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Adobe Primetime authentication 2.64.1リリースノート {#authn-264-rn}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

このページでは、このリリースの新機能、変更点および既知の問題について説明します。

## サーバー側および Web クライアント {#server-side-web-clients-2641}

* [ビルド番号](#build-number-2641)
* [リリースの概要](#release-overview-2641)

### ビルド番号 {#build-number-2641}

Adobe Primetime認証：adobe-pass-**2.64.1**
リリース日： **01/31/2023 - 02/02/2023**

### リリースの概要 {#release-overview-2641}

このリリースでは、次の機能が追加されました。

* SAML アサーションに&quot;in_response_to&quot;パラメーターがない MVPD からの未承諾認証応答をブロックする機能。
* セキュリティ要件に準拠するために、redirect_url パラメーターに対する検証が改善されました。
* 第 2 の画面認証要求に対するデバイス情報のログを、第 1 のデバイスから提供される情報を用いて改善した。

---
description: テスト中の一般的な問題には、多くの場合、ExpressPlay 認証子、トランスポートプロトコル、必要なサービスリクエストパラメーターが含まれます。
title: クイックスタートのトラブルシューティング
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# クイックスタートのトラブルシューティング{#troubleshooting-your-quick-start}

テスト中の一般的な問題には、多くの場合、ExpressPlay 認証子、トランスポートプロトコル、必要なサービスリクエストパラメーターが含まれます。

次の場合、 [!DNL curl] トークン生成のための ExpressPlay へのリクエストが失敗した場合、応答本文には、失敗の理由を説明するエラーメッセージが含まれます。

トークンの生成に成功したが、コンテンツがまだ再生されない場合は、ExpressPlay トークンの引き換えログで「期限切れのトークン」などのエラーを確認します。

トークンの生成に成功し、引き換えにエラーが発生しなかったがビデオが再生されない場合は、CEK がコンテンツと一致し、コンテンツの形式がターゲットデバイスの機能と一致していることを確認します。

さらに、次の情報も含まれます。

* サービスリクエストで正しい顧客認証子を使用していることを確認します。 テスト用認証子を使用する場合、本番用認証子を誤って使用するのは簡単です。 また、 *あなたの* 認証子。 例えば、テスト中に別のユーザーの `curl` コマンドを実行して、自分の認証子を自分の用に置き換えるのを忘れてください。

* リクエストまたはマニフェストで適切なトランスポートプロトコルを使用していることを確認します ( `https://` 対比 `https://`FairPlay の場合は `skd://` 対比 `https://` 対比 `https://`.

* 作業中の DRM ソリューションに必要なクエリーパラメーターがすべて含まれていることを確認します。 例えば、PlayReady と Widevine はどちらも DASH で動作するので混乱しやすくなりますが、必要なリクエストパラメーターとパッケージの設定は異なります。
* ExpressPlay アカウントに十分なトークンのクレジットがあり、使い果たされていないことを確認します。
* TVSDK に送信される DRM データの 3 重項が正しいことを確認します（ExpressPlay トークン、ライセンスサーバーの URL、DRM タイプ）。
* テストと実稼動の 2 つの環境があるので、ExpressPlay 環境が使用されていることをすべてのコンポーネントが同じ想定していることを確認します。
* 通常、異なるブラウザーは DASH コンテンツに対して 1 つの DRM のみをサポートします。
* TVSDK 2.4 以降では、DASH-LIVE パッケージプロファイルのみがサポートされます。 （DASH-OnDemand のサポートはロードマップに記載されています。）
* AndroidTV PlayReady のサポートは、デバイスの製造元の制限により、断続的に発生します。 例を挙げるには

   * Razer Forge デバイスに PlayReady コンテンツの問題がある
   * Amazon FireTV は、オーディオトラックが暗号化された DASH コンテンツを使用できません

* TVSDK 2.4 以降では、通常、AndroidTV デバイスのみが PlayReady と Widevine の両方の DRM をサポートします。 他のすべての Android デバイスは通常、Widevine のみをサポートします。
* TVSDK 2.4 以降、Android TVSDK は現在、PSSH ボックスが.mpd マニフェストに含まれている必要があります。 これは、DASH 標準に反します。DASH 標準では、PSSH ボックスは、.mpd 内だけでなく、コンテンツ自体の中の任意の場所に配置できることを指定します。

---
title: 用語集
description: 同時実行監視の用語集
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---


# 用語集 {#glossary}

## アカウント ID {#accid-defn}

* 購読者の MVPD アカウント。通常、実際の請求アカウントに対応します。 このアカウントは、MVPD が独自のシステムで識別できる必要があります。

## アクション {#action-defn}

* 件名が要求するアクセスのタイプ。CM に指定できる値は次のとおりです。 ***開始*** または ***続行*** ストリーミングセッション。

## アクティブストリーム {#active-stream-defn}

* 過去 90 秒間に少なくとも 1 つのイベント（ハートビート）を受信したストリーム。

* ***注意：*** ストリーム内の最後のイベントのタイプが stop (`?event=stop`) の場合、カウントされません。 これは、プレーヤーがストリームを明示的に閉じて、「アクティブ」と見なされなくなるようにする最適化です。

## アプリ {#application-defn}

* ビデオコンテンツへのアクセス用にテナントによって開発されました
* 同時実行監視サービスが提供する情報に基づいて、コンテンツアクセスに関する決定を行い、実施します ( これは、 [ポリシー情報ポイント](/help/concurrency-monitoring/policy-info-pt-versionone.md) ケース )
* 固有の **アプリケーション ID** Adobeが提供

## 同時実行監視サービス {#cm-service-defn}

* 購読者の監視システムとして機能し、MVPD と Programmers を、アプリケーション間のポリシー強制要件でサポートします。
* ストリームアクティビティを示すハートビートを受け取ります。
* としての機能 _ポリシーの決定ポイント_ ユーザーのアクティビティに基づいて認証リクエストを評価し、許可/拒否の応答を提供することで、
* としての機能 _ポリシー情報ポイント_ サブスクライバーのアクティブストリームの数（および追加のストリームメタデータ）を報告する方法。

## 環境 {#env-defn}

* 設定やシステム時間など、リクエストに関連する追加情報です。

## MVPD {#mvpd-defn}

* マルチチャンネルビデオプログラミングディストリビュータ。
* 認証および承認プロバイダーとしての役割を果たしますが、サービスまたはコンテンツプロバイダーの役割も果たします。

## ポリシー {#policy-defn}

* CM で定義されたコアアクセス制御概念（ターゲットとして定義）および一意の名前でグループ化された 1 つ以上のルール。

## ポリシー管理ポイント (PAP) {#policy-admin-pt-defn}

* アクセス認証ポリシーを管理するポイント。 この情報はここには記載されませんが、最終的には、お客様がアクセスポリシーを管理するためのセルフサービスコンソールを提供する予定です。

## ポリシー決定ポイント (PDP) {#policy-decn-pt-defn}

* アクセスの決定を発行する前に、承認ポリシーに対するアクセス要求を評価するポイント。

## ポリシー強制ポイント (PEP) {#policy-ef-pt-defn}

* リソースに対するユーザーのアクセス要求を傍受し、PDP に対して判定要求をおこない、要求に対してその判定を強制するポイント。 これは現在クライアントアプリケーションであり、この役割を同時実行監視に転送する計画はありません。

## ポリシー情報ポイント (PIP) {#policy-info-pt-defn}

* 属性値のソース。 同時実行監視は、次の情報を提供することで、情報ポイントとして機能します。
   * パススルーストリームメタデータ。
   * 同時ストリームに関するアクティビティ指標。

## プログラマー {#programmer-defn}

* サービスおよびコンテンツプロバイダーとしての役割を果たします。
* 同時実行監視サービスと統合され、デプロイ済みのクライアントアプリケーションに基づいて、上記のサービスデータに基づいて定義済みのセキュリティポリシーを実施します。
* 購読者のアクティビティを収集し、プロパティに制限ルールを適用する際に、MVPD をサポートする必要があります。
* また、すべてのターゲット・ポータルにわたるコンテンツへの同時アクセスを、別のルールとして制限することにも関心を持つ場合があります。

  *Q：残りのAdobe Primetime認証で、要求者 ID ではなくプログラマー ID が同じなのはなぜですか。*

  *A：プログラマーが、このパラメーターを使用できるようにして、使用例に応じて、プロパティ間で柔軟にデータを渡したり、分離したりできるようにするからです。*

## リソース {#resource-defn}

* 主体が消費したい実際のコンテンツ。 リソースには通常、所有者（発行者）に関連する属性が含まれ、ジャンルやその他の情報が提供される場合もあります。

## ルール {#rule-defn}

* 特定のストリームおよび関連するユーザーアクティビティに対して評価され、そのストリームに対するアクセスを許可するか拒否するかを決定するためのブール関数。

## ストリーミングセッション {#streaming-session-defn}

* 特定のリソースを消費するために主体が開始するストリーミングビデオセッション。

## 件名 {#subj-defn}

* インターネットを介した（ビデオ）コンテンツの利用者。 我々は意図的にその言葉を避けている _**ユーザー**_&#x200B;と同様に、同時実行監視は通常、MVPD アカウント ID( 同じ契約を共有する複数の実際のユーザー（例えば、世帯の家族メンバー）を扱います ) を扱います。

* ストリームごとに、サービスを利用する実際の人物に関連する属性や、そのネットワーク接続デバイスなどを使用して、被写体を拡張することができます。

## 購読者 {#subscriber-defn}

* MVPD の支払いを受けている顧客、または支払いを受けている顧客の資格情報を共有する人
* 上記のサービスを使用するクライアントアプリケーションによって、同時実行監視サービスによるコンテンツの視聴を停止できます。
* ベストケースのシナリオでは、同時実行監視サービスの存在に気付かない

## Target {#target-defn}

* ルールが特定のストリームに適用できるかどうかを返すストリーム述語。 CM の暗黙のターゲットは、問題のポリシーを参照するアプリケーションによって作成された任意のストリームです。 また、ルールを適用する前にアクティビティのフィルターを微調整するために、属性値の条件を追加できます。

## テナント {#tenant-defn}

* 同時実行監視のお客様の組織。

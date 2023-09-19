---
title: 参照実装 DB の更新
description: 参照実装 DB の更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# 参照実装 DB の更新{#update-the-reference-implementation-db}

指定されたユーザに対してライセンスが発行される使用モデルを制御するには、参照実装データベースにエントリを追加します。

1. エントリを `Customer` 表。

   The `Customer` この表には、ユーザーを認証するためのユーザー名とパスワードが含まれています。 また、ユーザーがサブスクリプション ( *購読* 使用モデル )。

1. 「ダウンロード先 — 自社」または「ビデオオンデマンド」の使用モデルでユーザーにアクセス権を付与します。

       「CustomerAuthorization」テーブルに次の項目を追加します。
   
   * 使用モデル
   * ユーザーがアクセスできるコンテンツの各セグメント

各テーブルにデータを入力する方法について詳しくは、 [!DNL PopulateSampleDB.sql] スクリプト (Primetime DRM DVD の [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] ディレクトリ ) に書き込まれます。

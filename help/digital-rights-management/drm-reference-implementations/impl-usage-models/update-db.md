---
title: 参照実装DBの更新
description: 参照実装DBの更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# 参照実装DB{#update-the-reference-implementation-db}を更新します

指定されたユーザに対してライセンスが発行される使用モデルを制御するには、参照実装データベースにエントリを追加します。

1. &lt;a0追加/>テーブルへのエントリ。`Customer`

   `Customer`テーブルには、ユーザーを認証するためのユーザー名とパスワードが含まれます。 また、購読(*購読*&#x200B;の使用モデルで発行されるライセンス)があるかどうかも示します。

1. 所有者へのダウンロードまたはビデオオンデマンドの使用モデルでユーザーアクセスを許可します。

       次を追加指定する&#39;CustomerAuthorization&#39;テーブルのエントリ：
   
   * 使用モデル
   * ユーザーがアクセスできるコンテンツの各セグメント

各テーブルにデータを埋め込む方法について詳しくは、[!DNL PopulateSampleDB.sql]スクリプト（[!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/]ディレクトリのPrimetime DRM DVDに含まれています）を参照してください。

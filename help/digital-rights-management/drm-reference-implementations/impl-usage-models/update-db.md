---
seo-title: 参照実装DBの更新
title: 参照実装DBの更新
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

---
seo-title: 参照実装DBの更新
title: 参照実装DBの更新
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 参照実装DBの更新{#update-the-reference-implementation-db}

指定されたユーザに対してライセンスが発行される使用モデルを制御するには、参照実装データベースにエントリを追加します。

1. テーブルにエントリを追加 `Customer` します。

   この表には、 `Customer` ユーザーを認証するためのユーザー名とパスワードが含まれています。 また、ユーザが購読(購読の使用モデルで発行されるライセンス ** )を持っているかどうかも示します。

1. ダウンロード先またはビデオオンデマンドの使用モデルで、ユーザーにアクセスを許可します。

       &#39;CustomerAuthorization&#39;テーブルにエントリを追加して、次を指定します。
   
   * 使用モデル
   * ユーザーがアクセスできるコンテンツの各セグメント

各テーブルの埋め込み方法について詳しくは、スクリプト(デ [!DNL PopulateSampleDB.sql] ィレクトリ内のPrimetime DRM DVDに含まれている)を参照し [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] てください。

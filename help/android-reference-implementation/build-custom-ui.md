---
description: 参照実装フレームワークに基づいて、カスタムユーザーインターフェイスを簡単に構築できます。
title: カスタムユーザーインターフェイスの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# カスタムユーザーインターフェイスの作成 {#build-a-custom-user-interface}

参照実装フレームワークに基づいて、カスタムユーザーインターフェイスを構築できます。

次の機能の UI コンポーネントは、既に統合されています。

* クリック可能な広告
* 広告オーバーレイ
* 遅延バインディングオーディオ
* クローズドキャプション
* 上記のすべてのコンポーネントのリスナー

1. を編集します。 [!DNL PlayerFragment.java] ファイルを使用して、プレーヤーで使用する UI コンポーネントを初期化します。

1. を編集します。 [!DNL res/player/player_fragment.xml] ファイルを編集して、ユーザーインターフェイスをカスタマイズします。
1. プロジェクトを構築します。

>[!NOTE]
>
>UI をシークバーに変更するには、MarkableSeekBar クラスを編集します。 The [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) クラスは、スライダー、スライダーのサム、広告マーカーホルダー、キューマーカー、バッファー範囲、シーク範囲の背景を処理します。

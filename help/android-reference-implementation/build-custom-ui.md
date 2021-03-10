---
description: 参照実装フレームワークに基づくカスタムユーザーインターフェイスを簡単に構築できます。
title: カスタムユーザーインターフェイスの構築
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# カスタムユーザーインターフェイスの構築{#build-a-custom-user-interface}

参照実装フレームワークに基づいてカスタムユーザーインターフェイスを構築できます。

次の機能のUIコンポーネントは既に統合されています。

* クリック可能な広告
* 広告オーバーレイ
* 遅延バインディングオーディオ
* クローズドキャプション
* 上記のすべてのコンポーネントのリスナー

1. [!DNL PlayerFragment.java]ファイルを編集して、プレイヤーで使用するUIコンポーネントを初期化します。

1. [!DNL res/player/player_fragment.xml]ファイルを編集し、ユーザーインターフェイスをカスタマイズします。
1. プロジェクトをビルドします。

>[!NOTE]
>
>UIをシークバーに変更するには、MarkableSeekBarクラスを編集します。 [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html)クラスは、スライダー、スライダーのサム、広告マーカーホルダー、キューマーカー、バッファー範囲、シーク範囲の背景を処理します。
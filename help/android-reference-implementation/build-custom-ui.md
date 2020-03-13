---
description: 参照実装のフレームワークに基づいて、カスタムユーザーインターフェイスを簡単に構築できます。
seo-description: 参照実装のフレームワークに基づいて、カスタムユーザーインターフェイスを簡単に構築できます。
seo-title: カスタムユーザーインターフェイスの構築
title: カスタムユーザーインターフェイスの構築
uuid: b785f6a4-3ef8-4f7a-a087-0d6551da9750
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# カスタムユーザーインターフェイスの構築 {#build-a-custom-user-interface}

参照実装フレームワークに基づいてカスタムユーザーインターフェイスを構築できます。

次の機能のUIコンポーネントは既に統合されています。

* クリック可能な広告
* 広告オーバーレイ
* オーディオの遅延バインディング
* クローズドキャプション
* 上記のすべてのコンポーネントのリスナー

1. ファイルを [!DNL PlayerFragment.java] 編集して、プレイヤーで使用するUIコンポーネントを初期化します。

1. ファイルを編集し [!DNL res/player/player_fragment.xml] て、ユーザインターフェイスをカスタマイズします。
1. プロジェクトを構築します。

>[!NOTE]
>
>UIをシークバーに変更するには、MarkableSeekBarクラスを編集します。 MarkableSeekBarク [ラスは](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) 、スライダ、スライダのサム、広告マーカーホルダ、キューマーカー、バッファー範囲、シーク範囲の背景を処理します。
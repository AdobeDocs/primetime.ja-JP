---
description: 必要に応じて、QoSProvider から再生とデバイスの統計を読み取るようにプレーヤーを設定できます。
title: QoS 再生とデバイス統計の表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# QoS 再生とデバイス統計の表示 {#display-qos-playback-and-device-statistics}

必要に応じて、QoSProvider から再生とデバイスの統計を読み取るようにプレーヤーを設定できます。

The `QoSProvider` クラスは、フレームレート、プロファイルのビットレート、バッファリングに費やした合計時間、バッファリングの試行回数、最初のビデオフラグメントから最初のバイトを取得するのにかかった時間、最初のフレームのレンダリングに要した時間、現在のバッファ時間など、様々な統計を提供します。

リファレンス実装では、以下を提供します。 `QoSManager` QoS オーバーレイの表示を有効にできるクラス。 Settings ユーザーインターフェイスで QoS の表示を有効にすることもできます。

![](assets/qos-configuration.jpg)

The `QoSManager` は、デバイス情報の取得、メディアプレーヤーへの接続、最新の QoS 情報による更新によって、QoS 統計を追跡します。

**QoS 統計レポートを有効または無効にします**

1. QosManager を作成するか、ManagerFactory を使用して QoS レポートを有効にします。

   * QosManager を作成するには：
      * このアプリケーションは、広告ワークフロー機能を使用する必要があります

   QoSManager qosManager = new QosManagerOn();

   * ManagerFactory を使用して QoS 統計を表示するには、次の手順を実行します。

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >ブール値をに変更 `false` QoS レポートを無効にします。

2. イベントリスナーを追加します。

   `qosManager.addEventListener(qosManagerEventListener);`

3. QoS プロバイダーを作成し、プレーヤーアクティビティコンテキストに接続します。

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >プレーヤーのアクティビティが破壊される場合は、必ず [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) QOS プロバイダーをメディアプレーヤーから切り離してクリーンアップする場合。

**関連する API ドキュメント**

* [クラス QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [クラス QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)

---
description: 必要に応じて、QoSProviderから再生とデバイスの統計情報を読み取るようにプレイヤーを設定できます。
seo-description: 必要に応じて、QoSProviderから再生とデバイスの統計情報を読み取るようにプレイヤーを設定できます。
seo-title: QoS再生とデバイス統計の表示
title: QoS再生とデバイス統計の表示
uuid: 8fc45a2f-03d4-4fa0-979b-eb816419c4f7
translation-type: tm+mt
source-git-commit: e1c6ab1d50f9262aaf70aef34854cf293fb4f30d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# QoS再生とデバイス統計の表示 {#display-qos-playback-and-device-statistics}

必要に応じて、QoSProviderから再生とデバイスの統計情報を読み取るようにプレイヤーを設定できます。

この `QoSProvider` クラスは、フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリング試行回数、最初のビデオフラグメントからの最初のバイト取得に要した時間、最初のフレームのレンダリングに要した時間、現在のバッファリング時間など、様々な統計を提供します。

参照実装は、QoSオーバーレイの表示を有効にできる `QoSManager` クラスを提供します。 QoS表示は、設定ユーザーインターフェイスで有効にすることもできます。

![](assets/qos-configuration.jpg)

デバイス情報を取得し、メディアプレーヤに付加し、最新のQoS情報で更新することで、QoS統計を `QoSManager` 追跡します。

**QoS統計レポートの有効化または無効化**

1. QosManagerを作成するか、ManagerFactoryを使用してQoSレポートを有効にします。

   * QosManagerを作成するには：
      * このアプリケーションでは、広告ワークフロー機能を使用する必要があります

   QoSManager qosManager = new QosManagerOn();

   * ManagerFactoryを使用してQoS統計情報を表示するには：

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>、config、mediaPlayer);

   >[!NOTE]
   >
   >ブール値を変更してQoSレポートを `false` 無効にします。

2. 追加イベントリスナー：

   `qosManager.addEventListener(qosManagerEventListener);`

3. QoSプロバイダーを作成し、プレイヤーアクティビティコンテキストに接続します。

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >プレイヤーアクティビティを破棄する場合は、 [qosManager.destroyQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) を呼び出して、QOSプロバイダーをメディアプレイヤーから切り離してクリーンアップします。

**関連するAPIドキュメント**

* [QosManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [QosManagerOnクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)

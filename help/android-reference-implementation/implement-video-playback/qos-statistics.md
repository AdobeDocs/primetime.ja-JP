---
description: 必要に応じて、QoSProviderから再生とデバイスの統計を読み取るようにプレーヤーを設定できます。
seo-description: 必要に応じて、QoSProviderから再生とデバイスの統計を読み取るようにプレーヤーを設定できます。
seo-title: QoS再生とデバイス統計の表示
title: QoS再生とデバイス統計の表示
uuid: 8fc45a2f-03d4-4fa0-979b-eb816419c4f7
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# QoS再生とデバイス統計の表示 {#display-qos-playback-and-device-statistics}

必要に応じて、QoSProviderから再生とデバイスの統計を読み取るようにプレーヤーを設定できます。

このク `QoSProvider` ラスは、フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリング試行回数、最初のビデオフラグメントから最初のバイトを取得するのに要した時間、最初のフレームのレンダリングに要した時間、現在のバッファ長、バッファ時間など、様々な統計を提供します。

参照実装は、QoSオーバ `QoSManager` ーレイの表示を有効にできるクラスを提供します。 QoSの表示設定は、次のように設定ユーザーインターフェイスで有効にすることもできます。

![](assets/qos-configuration.jpg)

QpS統 `QoSManager` 計は、デバイス情報を取得し、メディアプレイヤに付加し、最新のQpS情報で更新することで追跡される。

**QoS統計レポートの有効化または無効化**

1. QosManagerを作成するか、ManagerFactoryを使用してQoSレポートを有効にします。

   * QosManagerを作成するには：
      * このアプリケーションは、広告ワークフロー機能を使用する必要があります
   QoSManager qosManager = new QosManagerOn();

   * ManagerFactoryを使用してQoS統計を表示するには：
   qosManager = ManagerFactory.getQosManager(
   <b>true</b>、config、mediaPlayer);

   >[!NOTE]
   >
   >ブール値を変更してQoSレポ `false` ートを無効にします。

2. イベントリスナーの追加：

   `qosManager.addEventListener(qosManagerEventListener);`

3. QoSプロバイダーを作成し、プレイヤーアクティビティコンテキストに接続します。

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >プレイヤーのアクティビティが破棄される場合は、 [qosManager.destroyQOSProviderを呼び出して](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) 、QOSプロバイダーをメディアプレイヤーから切り離してクリーンアップします。

**関連するAPIドキュメント**

* [QosManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [QosManagerOnクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)

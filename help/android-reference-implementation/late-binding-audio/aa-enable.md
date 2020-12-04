---
description: 代替オーディオ機能マネージャーを作成して、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。
seo-description: 代替オーディオ機能マネージャーを作成して、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。
seo-title: 遅延バインディングオーディオの統合
title: 遅延バインディングオーディオの統合
uuid: cd2e259a-2af4-4d7b-a856-79bd087e8ca6
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# 遅延バインディングオーディオを統合{#integrate-late-binding-audio}

代替オーディオ機能マネージャーを作成して、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。

* 代替オーディオマネージャーを作成するには：

   ```java
   AAManager aaManager = new AAManagerOn(); 
   ```

* ManagerFactoryを使用して代替オーディオを有効にするには、次のコード行が`PlayerFragment.java`ファイル内にあることを確認します。

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>true</b>,config, mediaPlayer);
   ```

   代替オーディオを無効にするには：

   ```java
   aaManager = ManagerFactory.getAAManager( 
   <b>false</b>,config, mediaPlayer);
   ```


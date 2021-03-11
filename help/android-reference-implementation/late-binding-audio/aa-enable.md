---
description: 代替オーディオ機能マネージャーを作成して、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。
title: 遅延バインディングオーディオの統合
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '71'
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


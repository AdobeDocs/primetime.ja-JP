---
description: 代替オーディオ機能マネージャーを作成することで、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。
title: 遅延バインディングオーディオの統合
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 0%

---

# 遅延バインディングオーディオの統合 {#integrate-late-binding-audio}

代替オーディオ機能マネージャーを作成することで、遅延バインディングまたは代替オーディオストリームをプレーヤーに統合できます。

* 代替オーディオマネージャを作成するには：

  ```java
  AAManager aaManager = new AAManagerOn(); 
  ```

* ManagerFactory を使用して代替オーディオを有効にするには、次のコード行が `PlayerFragment.java` ファイル：

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>true</b>,config, mediaPlayer);
  ```

  代替オーディオを無効にするには：

  ```java
  aaManager = ManagerFactory.getAAManager( 
  <b>false</b>,config, mediaPlayer);
  ```

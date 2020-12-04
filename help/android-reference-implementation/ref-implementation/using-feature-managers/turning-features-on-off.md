---
description: マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。
seo-description: マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。
seo-title: ManagerFactoryを使用して機能をオンまたはオフにする
title: ManagerFactoryを使用して機能をオンまたはオフにする
uuid: 385c2707-95f7-4628-8d25-67731151cb6a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# ManagerFactory{#turning-features-on-or-off-using-managerfactory}を使用して機能をオンまたはオフにする

マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。

次の例のenablement引数は、この機能を使用するかどうかを決定します。 falseの場合、機能マネージャは作成されますが、機能マネージャが作成されなかったかのように、プレイヤにデフォルトの機能だけを提供します。 trueの場合、機能マネージャが作成され、機能が有効になり、メディアプレイヤーは設定ファイルからの入力を受け入れます。

例えば、`com.adobe.primetime.reference.ui.player.PlayerFragment.java`ファイル内で次のように指定します。

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**APIドキュメント**: [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)
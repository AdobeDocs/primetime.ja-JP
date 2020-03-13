---
description: マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。
seo-description: マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。
seo-title: ManagerFactoryを使用した機能のオン/オフ
title: ManagerFactoryを使用した機能のオン/オフ
uuid: 385c2707-95f7-4628-8d25-67731151cb6a
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# ManagerFactoryを使用した機能のオン/オフ{#turning-features-on-or-off-using-managerfactory}

マネージャーファクトリを使用すると、コードを調べずに機能のオン/オフを切り替えることができます。

次の例のenablement引数は、この機能を使用するかどうかを指定します。 falseの場合、機能マネージャは作成されますが、機能マネージャが作成されなかったかのように、プレイヤにデフォルトの機能のみを提供します。 trueの場合、機能マネージャが作成され、機能が有効になり、メディアプレイヤは設定ファイルからの入力を受け付けます。

例えば、次のようにファイ `com.adobe.primetime.reference.ui.player.PlayerFragment.java` ル内：

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**APIドキュメント**:ManagerFactory [](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)
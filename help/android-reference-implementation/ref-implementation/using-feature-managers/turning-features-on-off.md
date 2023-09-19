---
description: マネージャーファクトリを使用して、コードを調べずに機能のオン/オフを切り替えることができます。
title: ManagerFactory を使用した機能のオン/オフ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# ManagerFactory を使用した機能のオン/オフ{#turning-features-on-or-off-using-managerfactory}

マネージャーファクトリを使用して、コードを調べずに機能のオン/オフを切り替えることができます。

以下の例のイネーブルメント引数は、機能を使用するかどうかを決定します。 false の場合、機能マネージャは作成されますが、機能マネージャが作成されなかった場合と同じように、プレーヤにデフォルトの機能のみを提供します。 true の場合は、機能マネージャが作成され、機能が有効になり、メディアプレーヤーは設定ファイルからの入力を受け付けます。

例えば、 `com.adobe.primetime.reference.ui.player.PlayerFragment.java` ファイル：

```java
adsManager = ManagerFactory.getAdsManager( 
<b>true</b>, config, mediaPlayer);
```

**API ドキュメント**: [ManagerFactory](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/ManagerFactory.html)

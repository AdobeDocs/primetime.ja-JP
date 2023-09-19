---
description: TVSDK 機能は設定によって駆動され、MediaPlayer を通じて実装されます。
title: 設定情報を MediaPlayer に渡して機能マネージャーを作成する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# 設定情報を MediaPlayer に渡して機能マネージャーを作成する {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

TVSDK 機能は設定によって駆動され、MediaPlayer を通じて実装されます。

* 設定は、ABR コントロールの初期ビットレートやデフォルトのクローズドキャプション表示など、機能固有の設定のリストです。

  機能マネージャは、機能の動作を決定するために、設定を取得する必要があります。

  Primetime リファレンス実装では、設定は共有の環境設定に保存されますが、環境に応じてどのような方法でも設定を保存できます。

* `MediaPlayer` は、ビデオリソースを格納する TVSDK メディアプレーヤーオブジェクトです。

  機能マネージャーは、 TVSDK イベントリスナーをこのプレーヤーオブジェクトに登録し、再生セッションからデータを取得し、 TVSDK 機能を再生セッションにトリガーします。

各機能には、対応する設定インターフェイスがあります。 例： `CCManager` uses `ICCConfig` 設定を取得します。 `ICCConfig` には、クローズドキャプションに関連する設定情報のみを取得するメソッドが含まれています。

次の例は、 [!DNL ICCConfig.java] クローズドキャプションの表示、フォントスタイル、フォントエッジに関する情報を `MediaPlayer`:

```java
// Constructor of CCManager 
 
<b>public CCManager(ICCConfig ccConfig, MediaPlayer mediaPlayer) {...}</b> 
  
// ICCConfig methods 
 
<b>public interface ICCConfig {</b> 
  
    /** 
     * Get the closed captioning visibility config 
     * 
     * @return true if visibility is set to true, false otherwise 
     */ 
    
<b> public boolean getCCVisibility();</b> 
  
    /** 
     * Get the closed captioning font style 
     * 
     * @return TextFormat.Font object represents font style 
     */ 
     
<b>public TextFormat.Font getCCFont();</b>

    /** 
     * Get the closed captioning font edge 
     * 
     * @return TextFormat.FontEdge represents of font edge 
     */ 
     
<b>public TextFormat.FontEdge getCCFontEdge();</b> 
... 
}
```

TVSDK 機能を使用するアプリケーションは、設定プロバイダーと `MediaPlayer` オブジェクト。 例：

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

機能マネージャー設定 API ドキュメント： [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)

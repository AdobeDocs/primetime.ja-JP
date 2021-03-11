---
description: この節では、設定の概念と形式を説明するサンプル設定を示します。
title: RBOP設定の例
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# RBOP設定の例{#sample-rbop-configuration}

この節では、設定の概念と形式を説明するサンプル設定を示します。

以下のサンプルJSON設定は、以下を指定するピクセル出力ポリシーを定義しています。

* ビデオの復号化を1080以下の解像度に制限する
* 720と480の解像度に特定の制約を課す：

   * 解像度720の場合：デジタル出力にはHDCPが必要&#x200B;*コピー生成管理システム — アナログ* (CGMS-A)保護を必要とします。
   * 解像度480の場合：デジタル出力にはHDCPが必要アナログの保護を必要としない

```
{ 
  "pixelConstraints":  
    [ 
      { 
        "pixelCount": 720, 
        "digital": 
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "REQUIRED_CGMSA"} 
      }, 
      { 
        "pixelCount": 480, 
        "digital":  
          [ 
            {"output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}} 
          ], 
        "analog": {"output": "NO_PROTECTION"} 
      } 
    ], 
  "maxPixel": 1080 
}
```

上記のサンプル設定については、以下の点に注意してください。

* `pixelCount`仕様は、JSON構造の1レベル下の`pixelConstraints`セクション内です。

* 各ピクセル数仕様の中で、デジタル出力とアナログ出力の両方に対して出力保護を指定する。
* デジタル出力仕様では、HDCPバージョンが指定されていますが、クライアントは現在HDCPバージョン設定をサポートしていません。 詳しくは、FAQを参照してください。


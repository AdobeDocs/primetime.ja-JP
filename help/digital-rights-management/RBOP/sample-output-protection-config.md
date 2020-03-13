---
description: この節では、設定の概念と形式を示すサンプル設定を示します。
seo-description: この節では、設定の概念と形式を示すサンプル設定を示します。
seo-title: RBOPの設定例
title: RBOPの設定例
uuid: fa5ead93-36c5-4ad1-947b-c4f1f2632d9b
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOPの設定例 {#sample-rbop-configuration}

この節では、設定の概念と形式を示すサンプル設定を示します。

次のサンプルJSON設定では、次の内容を指定するピクセル出力ポリシーを定義しています。

* ビデオの復号化を1080以下の解像度に制限する
* 720と480の解像度に特定の制約を課す：

   * 解像度720の場合：デジタル出力にHDCPが必要require *Copy Generation Management System — アナログ出力用のAnalog* (CGMS-A)保護。
   * 解像度480の場合：デジタル出力にHDCPが必要アナログの保護を必要としない

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

上記の設定例について、次の点に注意してください。

* 指定 `pixelCount` は、JSON構造の1レベル下のセクション内にあり `pixelConstraints` ます。

* 各ピクセル数仕様の中で、デジタル出力とアナログ出力の両方に対して出力保護を指定する。
* デジタル出力仕様では、HDCPバージョンが指定されていますが、クライアントは現在HDCPバージョンをサポートしていません。 詳しくは、FAQを参照してください。


---
description: この節では、設定の概念と形式を説明するサンプル設定を示します。
title: RBOP 設定のサンプル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# RBOP 設定のサンプル {#sample-rbop-configuration}

この節では、設定の概念と形式を説明するサンプル設定を示します。

以下のサンプル JSON 設定は、以下を指定するピクセル出力ポリシーを定義します。

* ビデオの復号化を解像度 1080 以下に制限する
* 解像度 720 と 480 に特定の制約を課す：

   * 解像度 720 の場合：デジタル出力には HDCP が必要、必要 *コピー生成管理システム — アナログ* (CGMS-A) アナログ出力用の保護。
   * 480 解像度の場合：デジタル出力には HDCP が必要。アナログの保護は不要

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

上記のサンプル設定に関して、次の点に注意してください。

* The `pixelCount` の仕様は、JSON 構造の 1 レベル下、 `pixelConstraints` 」セクションに入力します。

* 各ピクセルカウント仕様内で、デジタル出力とアナログ出力の両方に対して出力保護を指定する。
* デジタル出力仕様では、HDCP バージョンが指定されていますが、クライアントは現在 HDCP バージョン管理をサポートしていません。 詳しくは、 FAQ を参照してください。

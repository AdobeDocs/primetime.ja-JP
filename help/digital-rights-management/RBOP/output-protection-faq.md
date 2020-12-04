---
description: 解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。
seo-description: 解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。
seo-title: RBOP FAQ
title: RBOP FAQ
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: fa9e89dd63c8b4c9d6eee78258957cfd30c29088
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# RBOP FAQ {#rbop-faq}

解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。

* **Q.ピクセル制約のデジタル出力要件を定義する** *とき、HDCPバージョンを残しても、HDCP要件がないと解析/フォーマットエラーが発生します。この場合、デジタル出力要件はどのように設定する必要がありますか。* **A.現在、HDCPバージョンチェックはクライアントではサポートされていない** ので、AdobeではHDCPバージョンをに設定することをお勧め `1.0`します。これにより、HDCPのバージョンチェックがサポートされる場合、設定が正しくフォーマットされ、セマンティック上の一貫性が確保されます。 次のスニペットは、このHDCP値の設定を示しています。

   ```
   { "pixelConstraints":  
     [  
       { "pixelCount": 720, "digital":  
         [  
           {  
             "output": "REQUIRED", "hdcp": {"major": 1, "minor": 0}  
           }  
         ]  
       }  
     ]  
   }
   ```

* **Q. RBOPのピクセル制約** *は、個別のものですか、それとも範囲に基づいていますか。* **A.** RBOPピクセル制約の幅は、各ピクセル数は、指定された数以下、または2つ以上のピクセル数制約がある場合はその値より小さい最大数までのすべてのピクセル数の要件を定義します。 単純に言うと、値は各垂直ピクセル数の最大しきい値として適用されます。

   垂直解像度が240、480、600、720、1080のMBRストリームが、以下のRBOP設定を使用してプレイヤーに渡されるとします。

   **RBOPポリシーの設定：**

   * 720P - HDCPが必要
   * 480P - OPなし

   次のルールが各バリアントに適用されます。

   **ストリーム：**

   * 240、480:どちらも&lt;= 480;OPは不要で、HDCPが存在するかどうかにかかわらず、ストリームが読み込まれます。
   * 600, 720:どちらも&lt;= 720;再生にはHDCPが必要です
   * 1080:> 720;ストリームが上記のルールに見つからないので、ブロックリスト（エラーが返されます）に表示されます。


* **Q.** 一部のAndroidデバイスで、定義したピクセル数の制限が、定義したとおりに適用されていません。何が起きてる？

   **A.** 一部のAndroidデバイスは、レポートのフレームサイズが通常のサイズよりもやや大きくなります。この状況を修正するには、フレームサイズ（`maxPixel`設定と`pixelCount`設定）を20ピクセル上に調整します。 例えば、フレームサイズの設定を次の値から上方に調整します。

   ```
   { 
       "maxPixel": 800, 
       "pixelConstraints": [ 
           { "pixelCount": 532, 
             "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
             "analog": {"output": "REQUIRED"} 
           }, 
   ... 
   ```

   終了：

   ```
   { 
       "maxPixel": 820, 
       "pixelConstraints": [ 
           { "pixelCount": 552, 
             "digital": [{"output": "REQUIRED", "hdcp":{"major": 1,"minor": 0}}], 
             "analog": {"output": "REQUIRED"} 
           }, 
   ... 
   ```

   を通して、`maxPixel`と`pixelCount`のすべてのインスタンスに対して。


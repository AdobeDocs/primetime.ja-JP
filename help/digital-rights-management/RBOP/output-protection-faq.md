---
description: 解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。
seo-description: 解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。
seo-title: RBOP FAQ
title: RBOP FAQ
uuid: 7dcd337c-369a-474c-8768-409c48b5cee5
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOP FAQ {#rbop-faq}

解像度ベースの出力保護の使用に関するよくある質問(FAQ)です。

* **問い** ピクセ *ル制約のデジタル出力要件を定義する際に、HDCPバージョンを残しておくと解析/フォーマットエラーが発生しますが、HDCPの要件がありません。 この場合、デジタル出力の要件をどのように設定すればよいですか。* **A.** 現在、HDCPバージョンの確認はクライアントでサポートされていないので、HDCPバージョンをに設定することをお勧めしま `1.0`す。 これにより、HDCPのバージョンチェックがサポートされている場合、設定が正しくフォーマットされ、将来的にセマンティック上の一貫性が確保されます。 次のスニペットは、このHDCP値の設定を示しています。

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

* **問い** RBOPのピクセ *ル制約は、個別のものか、または範囲ベースのものか。* **A.** RBOPのピクセル制限は、幅に基づいて適用されます。 各ピクセル数は、指定した数値以下、または1つ以上のピクセル制約がある場合はその値より小さい最大数までのすべてのピクセル数の要件を定義します。 簡単に言うと、値は各垂直ピクセル数の最大しきい値として適用されます。

   垂直解像度が240、480、600、720、1080のMBRストリームが、以下のRBOP設定を使用してプレイヤーに渡されるとします。

   **RBOPポリシーの設定：**

   * 720P - HDCPが必要
   * 480P - OPなし
   次のルールが各バリアントに適用されます。

   **ストリーム：**

   * 240、480:どちらも&lt;= 480;opは不要で、HDCPが存在するかどうかにかかわらず、ストリームが読み込まれます。
   * 600、720:どちらも&lt;= 720;再生にはHDCPが必要です
   * 1080:> 720;ストリームは上記のルールに見つからないので、ブラックリストに記載されています（エラーが返されます）。


* **問い** 一部のAndroidデバイスで、定義したピクセル数制限が、定義どおりに適用されていません。 何が起きてる？

   **A.** 一部のAndroidデバイスでは、通常のサイズよりも少し大きいフレームサイズがレポートされます。 この状況を修正するには、フレームサイズ(および設 `maxPixel` 定)を `pixelCount` 上方向に20ピクセル調整します。 例えば、次のフレームサイズ設定を上に調整します。

   ```
   { 
       "maxPixel":  
   
<b>800</b>,&quot;pixelConstraints&quot;:[{ &quot;pixelCount&quot;:\
<b>532</b>,&quot;digital&quot;: [{&quot;output&quot;:&quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;:1,&quot;minor&quot;:0}}],&quot;analog&quot;:{&quot;output&quot;:&quot;必須&quot;}},...

```
to: 
```
{&quot;maxPixel&quot;:\
<b>820</b>,&quot;pixelConstraints&quot;:[{ &quot;pixelCount&quot;:\
<b>552</b>,&quot;digital&quot;: [{&quot;output&quot;:&quot;REQUIRED&quot;, &quot;hdcp&quot;:{&quot;major&quot;:1,&quot;minor&quot;:0}}],&quot;analog&quot;:{&quot;output&quot;:&quot;必須&quot;}},...

```
throughout, for all instances of `maxPixel` and `pixelCount`.


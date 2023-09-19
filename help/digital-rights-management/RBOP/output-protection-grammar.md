---
description: この節では、設定入力の文法について説明し、有効な入力オプションと無効な入力オプションを強調し、省略されたオプションフィールドの解釈方法を説明します。
title: RBOP 文法
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# RBOP 文法 {#rbop-grammar}

この節では、設定入力の文法について説明し、有効な入力オプションと無効な入力オプションを強調し、省略されたオプションフィールドの解釈方法を説明します。

解像度ベースの出力保護文法は、一連のルールとして定義されます。各ルールは、複数の有効な形式を持つことができます。

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## 文法規則の適用 {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>文法を読みやすくするために、次のプロパティは文法に反映されませんが、まだ true のままです。

1. オブジェクト内で定義されたペアの順序は固定されないので、ペアの順列はすべて有効です。

   例えば、次のようなオブジェクトを定義した場合、

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   次の構造も有効と見なされます。 =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. オブジェクト内の各ペアについて、そのペアの 1 つのインスタンスが、特定のオブジェクトの特定のインスタンス内に存在すると想定されます。

   例えば、次のようなオブジェクトを定義した場合、

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   次のインスタンスは、2 つあるので無効になります。 `foo` 同じオブジェクト内のペア：

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   同様に、次の 2 つのオブジェクトがあります。

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   および：

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

   は有効です。同じオブジェクトの独立したインスタンスであるからです。

1. 1 つ以上の文字列のシーケンスを選択できる定義については、文字列をセットのように扱います。セット内で重複するエントリは単一のエントリとして扱われます。 例： `["foo", "bar", "foo", "baz"]` はと同じです。 `["foo", "bar", "baz"]`

1. 数値を定義する場合は、ルール間にスペースが使用されます ( 例： `Digit Digits`) ですが、ルールを適用する際には、このようなスペースを使用しないでください。

   例えば、 *百二十三* NonZeroInteger ルールに従って、次のように表現する必要があります。 `123` ではなく `1 2 3`を返します。

1. 一部のルールでは複数のフォームを使用できます。 この場合、異なるフォームは `'|'` 文字。

   例えば、次のルールがあります。

   ```
   Foo ::= "A" | "B" | "C"
   ```

   は、のインスタンスを意味します。 `Foo` は、「A」、「B」、「C」に置き換えることができます。 これは、複数行にわたるフォームと混同しないでください。これは、より長いフォームをより読みやすくするための機能です。

## 文法 {#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

```
PixelBasedOPConfig ::= 
      {} 
    | { "maxPixel": NonNegativeInteger } 
    | { "pixelConstraints": PixelConstraintsSeq } 
    | { "pixelConstraints": PixelConstraintsSeq, 
        "maxPixel": NonNegativeInteger } 
 
PixelConstraintsSeq ::= 
      [] 
    | [ PixelConstraints ] 
 
PixelConstraints ::= 
      PixelConstraint 
    | PixelConstraint, PixelConstraints 
 
PixelConstraint ::= 
      { "pixelCount": NonNegativeInteger } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
         "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
 
DigitalOutputRestrictionsSeq ::= 
      [] 
    | [ DigitalOutputRestrictions ] 
 
DigitalRestrictions ::= 
      DigitalRestriction 
    | DigitalRestriction, DigitalRestrictions 
 
DigitalRestriction ::= 
      { "output": DigitalOutputOption } 
    | { "output": DigitalOutputOption, "hdcp": HDCP } 
 
DigitalOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "REQUIRED" 
    | "NO_PLAYBACK" 
 
HDCP ::= 
    { "major": PositiveInteger, "minor": NonNegativeInteger } 
 
AnalogOutputRestriction ::= 
    { "output": AnalogOutputOption } 
 
AnalogOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "USE_IF_AVAILABLE_ACP" 
    | "USE_IF_AVAILABLE_CGMSA" 
    | "REQUIRED" 
    | "REQUIRED_ACP" 
    | "REQUIRED_CGMSA" 
    | "NO_PLAYBACK" 
 
OTAOutputRestriction ::= 
    { "whitelist": OTAWhitelistSeq } 
 
OTAWhitelistSeq ::= 
      [] 
    | [ OTAWhitelist ] 
 
OTAWhitelist ::= 
      OTAConnectionType 
    | OTAConnectionType, OTAWhitelist 
 
OTAConnectionType ::= 
      "MIRACAST" 
    | "AIRPLAY" 
    | "WIDI" 
    | "DLNA" 
 
NonNegativeInteger ::= 
      Digit 
    | NonZeroDigit Digits 
 
PositiveInteger ::= 
      NonZeroDigit 
    | NonZeroDigit Digits 
 
Digits ::= 
      Digit 
    | Digit Digits 
 
Digit ::= 
      0 
    | NonZeroDigit

NonZeroDigit ::= 
      1 
    | 2 
    | 3 
    | 4 
    | 5 
    | 6 
    | 7 
    | 8 
    | 9
```

## セマンティクス：有効な設定ですが無効な設定です {#section_709BE240FF0041D4A1B0A0A7544E4966}

The *出力保護の設定例* トピックでは、有効な設定とその意味を示していました。 前の節 ( *この* このトピックでは、設定の文法規則について説明しました。 文法は構文の正確性を確保するのに役立ちますが、意味的に正しくない（つまり、論理的でない）構文的に正しい設定があります。 この節では、 *構文的に* 法的ですが *意味的に* 間違っています。 この節の例は、議論中のシナリオを説明するのに必要な最小の構造に減少したことに注意してください。

* 同じピクセル数で複数のピクセル制約を定義することは無効です。

  ```
  {  
    "pixelConstraints":  
      [  
        { "pixelCount": 720 }  
      ]  
   }  
  ```

* ピクセル数は、指定された最大ピクセル解像度を超えてはなりません。

  ```
  { 
    "maxPixel": 720, 
    "pixelConstraints": 
      [ 
        {"pixelCount": 1080} 
      ] 
  } 
  ```

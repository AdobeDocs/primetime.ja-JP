---
description: この節では、設定入力の文法、有効な入力オプションと無効な入力オプションの強調、および省略されたオプションフィールドの解釈方法について説明します。
seo-description: この節では、設定入力の文法、有効な入力オプションと無効な入力オプションの強調、および省略されたオプションフィールドの解釈方法について説明します。
seo-title: RBOP文法
title: RBOP文法
uuid: d9064e39-593a-4767-b835-287640b4c94a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOP文法 {#rbop-grammar}

この節では、設定入力の文法、有効な入力オプションと無効な入力オプションの強調、および省略されたオプションフィールドの解釈方法について説明します。

解像度ベースの出力保護の文法は、一連のルールとして定義され、各ルールに複数の有効なフォームを含めることができます。

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## 文法規則の適用 {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>文法の読みやすさを向上させるために、次のプロパティは文法に反映されませんが、trueを保持します。

1. オブジェクト内で定義されたペアの順序は固定されません。これにより、ペアの任意の順列が有効となる。

   例えば、次のようなオブジェクトを定義したとします。

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   次の構造も有効と見なされます。=

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. オブジェクト内の各ペアについて、そのペアの1つのインスタンスのみが、特定のオブジェクトの特定のインスタンス内に存在すると見なされます。

   例えば、次のようなオブジェクトを定義したとします。

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   同じオブジェクト内に2つのペアが存在するので、次のインスタ `foo` ンスは無効になります。

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   同様に、次の2つのオブジェクトを持ちます。

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

   は、同じオブジェクトの独立したインスタンスであるため有効です。

1. 1つ以上の文字列のシーケンスを選択できる定義の場合、文字列をセットのように扱い、重複するエントリは単一のエントリとして扱います。 例えば、 `["foo", "bar", "foo", "baz"]` は `["foo", "bar", "baz"]`

1. 数値を定義する場合、ルール間にスペースが使用されます(例： `Digit Digits`)が、ルールを適用する際にはスペースを使用しないでください。

   例えば、NonZeroIntegerルールごとに123の数値を表す場合 *、ルールにNonZeroDigitとDigitsの間にスペースが含まれていても、*`123``1 2 3`NonZeroIntegerルールではなく、23の数値を表す必要があります。

1. 一部のルールでは複数のフォームを使用できます。 この場合、異なるフォームは文字で区切られ `'|'` ます。

   例えば、次のルールがあります。

   ```
   Foo ::= "A" | "B" | "C"
   ```

   は、のインスタンス `Foo` を「A」、「B」または「C」に置き換えることができることを意味します。 これは複数行にまたがるフォームと混同しないでください。これは、より長いフォームをより読みやすくする機能です。

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

## セマンティック：有効な設定ですが無効な設定です {#section_709BE240FF0041D4A1B0A0A7544E4966}

『 *Sample Output Protection Configuration* 』トピックでは、有効な設定とその意味を説明しています。 このトピックの前の節で *は* 、設定の文法規則について説明しました。 文法は構文の正確性を保証するのに役立ちますが、意味的に正しくない（つまり、論理的でない）構文的に法的な設定が存在します。 この節では、構文的には法的には正しいが *、意味的には正しくない設定につ* いて説明しま ** す。 この節の例は、検討中のシナリオを示すのに必要な最小構造に減らされたことに注意してください。

* 同じピクセル数を持つ複数のピクセル制約を定義することは無効です。

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

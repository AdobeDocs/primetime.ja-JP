---
description: この節では、設定入力の文法、有効な入力オプションと無効な入力オプションの強調、および省略されたオプションフィールドの解釈方法について説明します。
title: RBOP文法
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---


# RBOP文法{#rbop-grammar}

この節では、設定入力の文法、有効な入力オプションと無効な入力オプションの強調、および省略されたオプションフィールドの解釈方法について説明します。

解像度ベースの出力保護文法は、一連のルールとして定義されます。各ルールには、次の有効な複数の形式を含めることができます。

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## 文法規則の適用{#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>文法を読みやすくするために、次のプロパティは文法に反映されませんが、そのまま保持されます。

1. オブジェクト内で定義されるペアの順序は決まりません。これにより、ペアの並び替えが有効となる。

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

1. オブジェクト内の各ペアについて、そのペアの1つのインスタンスが、特定のオブジェクトの特定のインスタンス内に存在すると想定します。

   例えば、次のようなオブジェクトを定義したとします。

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   次のインスタンスは、同じオブジェクト内に2つの`foo`ペアがあるので無効になります。

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   同様に、次のような2つのオブジェクトがあります。

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

1. 1つ以上の文字列のシーケンスが選択される場合、重複エントリを1つのエントリとして扱うセットのように文字列を扱ってください。 例えば、`["foo", "bar", "foo", "baz"]`は`["foo", "bar", "baz"]`と同じです

1. 数値を定義する場合、ルール間にスペースを使用します（例：`Digit Digits`）が、ルールを適用する場合は、このようなスペースを使用しないでください。

   例えば、NonZeroIntegerルールごとに&#x200B;*123*&#x200B;という数値を表す場合、ルールにNonZeroDigitとDigitsの間にスペースが含まれていても、`1 2 3`ではなく`123`として表す必要があります。

1. 一部のルールでは、複数のフォームを使用できます。 この場合、異なるフォームは`'|'`文字で区切られます。

   例えば、次のルールがあります。

   ```
   Foo ::= "A" | "B" | "C"
   ```

   は、`Foo`のインスタンスを&quot;A&quot;、&quot;B&quot;、または&quot;C&quot;に置き換えることができることを意味します。 これは、複数行にまたがるフォームと混同しないでください。これは、より長いフォームをより読みやすくする機能です。

## 文法{#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

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

## セマンティック：正しい構成ですが無効な構成{#section_709BE240FF0041D4A1B0A0A7544E4966}

*サンプル出力保護の設定*&#x200B;のトピックでは、有効な設定とセマンティックの意味が示されています。 *この*&#x200B;トピックの前の節では、設定の文法規則を紹介しました。 文法は構文的な正確性を確保するのに役立ちますが、意味的に正しくない（つまり、論理的でない）構文的な法的な設定もあります。 この節では、*構文的には*&#x200B;法的には&#x200B;*法的には*&#x200B;法的には正しくないが、意味的には正しくない設定を示します。 この節の例は、検討中のシナリオを説明するのに必要な最小構造に減らされたことに注意してください。

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

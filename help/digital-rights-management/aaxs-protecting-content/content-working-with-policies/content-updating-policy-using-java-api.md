---
title: Java API を使用したポリシーの更新
description: Java API を使用したポリシーの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Java API を使用したポリシーの更新 {#updating-a-policy-using-the-java-api}

Java API を使用してポリシーを更新するには、次の手順を実行します。

1. 開発環境を設定し、 [開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) を選択します。
1. の作成 `Policy` インスタンスを作成し、ポリシーをファイルまたはデータベースから読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. を更新します。 `Policy` オブジェクトに割り当てる必要があります。

   ```java
     // Change the policy name.  
     policy.setName("UpdatedDemoPolicy");  
   
     // Add DRM module restrictions to the play right  
     for (Right r: policy.getRights()) {  
      if (r instanceof PlayRight) {  
       PlayRight pr = (PlayRight) r;  
       // Disallow Linux versions up to and including 1.9.  Allow  
       // all other OSes and Linux versions above 1.9  
       VersionInfo toExclude = new VersionInfo();  
       toExclude.setOS("Linux");  
       toExclude.setReleaseVersion("1.9");  
       Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
       exclusions.add(toExclude);  
       ModuleRequirements drmRestrictions = new ModuleRequirements();  
       drmRestrictions.setExcludedVersions(exclusions);  
       pr.setDRMModuleRequirements(drmRestrictions);  
       break;  
      }  
     }
   ```

1. 更新されたをシリアル化します。 `Policy` オブジェクトを作成し、ファイルまたはデータベースに保存します。

   ```java
      // Serialize the policy.  
      byte[] policyBytes = policy.getBytes();  
      System.out.println("New policy revision number: "  
       +  policy.getRevision());      
      // Write the policy to a file.   
      // Alternatively, the policy may be stored in a database.  
      FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
      out.write(policyBytes);  
      out.close(); 
   ```

このサンプルコードの完全なソースについては、 `com.adobe.flashaccess.samples.policy.UpdatePolicy` 「リファレンス実装」コマンドラインツールの「samples」ディレクトリ。

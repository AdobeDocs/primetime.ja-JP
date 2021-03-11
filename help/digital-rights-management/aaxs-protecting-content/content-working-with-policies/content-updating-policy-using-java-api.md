---
title: Java APIを使用したポリシーの更新
description: Java APIを使用したポリシーの更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# Java API {#updating-a-policy-using-the-java-api}を使用したポリシーの更新

Java APIを使用してポリシーを更新するには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内の[開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)で説明されているすべてのJARファイルを含めます。
1. `Policy`インスタンスを作成し、ポリシーをファイルまたはデータベースから読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. `Policy`オブジェクトのプロパティ（名前や使用ルールなど）を設定して、オブジェクトを更新します。

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

1. 更新した`Policy`オブジェクトをシリアル化し、ファイルまたはデータベースに格納します。

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

このサンプルコードの完全なソースについては、『リファレンス導入コマンドラインツール』の`com.adobe.flashaccess.samples.policy.UpdatePolicy`を参照してください。

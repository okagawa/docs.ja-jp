---
title: 軽減策:X509CertificateClaimSet.FindClaims メソッド
description: .NET Framework 4.6.1 を対象とするアプリで X509CertificateClaimSet.FindClaims メソッドがどのように変更されたかについて説明します。
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253571"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>軽減策:X509CertificateClaimSet.FindClaims メソッド

.NET Framework 4.6.1 以降を対象とするアプリの <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドでは、`claimType` 引数と SAN フィールド内のすべての DNS エントリの照合が試みられます。  
  
## <a name="impact"></a>影響  

 この変更によって影響を受けるのは、.NET Framework 4.6.1 以降のバージョンの .NET Framework を対象とするアプリのみです。  
  
 .NET Framework の以前のバージョンを対象とするアプリの場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> メソッドは、`claimType` 引数と最後の DNS エントリのみの照合を試みます。  
  
## <a name="mitigation"></a>軽減策  

 この変更が望ましくない場合は、.NET Framework 4.6.1 バージョン以降の .NET Framework を対象とするアプリで無効にできます。これは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 また、以前のバージョンの .NET Framework を対象とするものの、.NET Framework 4.6.1 以降のバージョンで実行されているアプリでは、そのアプリの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>関連項目

- [アプリケーションの互換性](application-compatibility.md)

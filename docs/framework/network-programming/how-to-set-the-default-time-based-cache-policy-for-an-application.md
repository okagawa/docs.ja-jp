---
description: '詳細情報: 方法:アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する'
title: '方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 1ca9504d8a6df20d3824230d5fb96eb0f13636eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662768"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する

既定の時間ベースのキャッシュ ポリシーにより、キャッシュされたリソースと共に送信されるヘッダーによってアプリケーションでキャッシュの動作を定義することができます。RFC 2616 のセクション 13 と 14 で定義されているキャッシュの動作については、[Internet Engineering Task Force (IETF)](https://www.ietf.org/) に関するページをご覧ください。 これは、ほとんどのアプリケーションの適切なキャッシュの動作です。  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>アプリケーションの既定の自動ポリシーを設定するには  
  
1. 既定の時間ベースのポリシー オブジェクトを作成します。  
  
2. アプリケーション ドメインの既定値として、ポリシー オブジェクトを設定します。  
  
## <a name="example"></a>例  

 このセクションの 2 つの例では、同一のポリシーを生成します。  
  
 次の例では、既定の時間ベースのポリシーを作成し、アプリケーション ドメインの既定値として設定します。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 次の例に示すように、<xref:System.Net.Cache.RequestCachePolicy> クラスを使用して既定の時間ベースのキャッシュ ポリシーを作成することもできます。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>関連項目

- [ネットワーク アプリケーションのキャッシュ管理](cache-management-for-network-applications.md)
- [キャッシュ ポリシー](cache-policy.md)
- [場所ベースのキャッシュ ポリシー](location-based-cache-policies.md)
- [時間ベースのキャッシュ ポリシー](time-based-cache-policies.md)
- [\<requestCaching> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
